# Calling C and Fortran Code

尽管大多数代码可以用 Julia 编写，但已经有许多高质量、成熟的数值计算库是用 C 和 Fortran 编写的。为了方便使用这些现有代码，Julia 使得调用 C 和 Fortran 函数变得简单高效。Julia 采用“无样板代码”的理念：函数可以直接从 Julia 调用，而无需任何“粘合”代码、代码生成或编译——即使是在交互式提示符下。这是通过使用适当的调用与 [`@ccall`](@ref) 宏（或不太方便的 [`ccall`](@ref) 语法，参见 [`ccall` syntax section](@ref ccall-interface)）来实现的。

要调用的代码必须作为共享库可用。大多数 C 和 Fortran 库已经以共享库的形式编译，但如果您使用 GCC（或 Clang）自己编译代码，则需要使用 `-shared` 和 `-fPIC` 选项。Julia 的 JIT 生成的机器指令与原生 C 调用的指令相同，因此由此产生的开销与从 C 代码调用库函数的开销相同。 [^1]

默认情况下，Fortran 编译器 [generate mangled names](https://en.wikipedia.org/wiki/Name_mangling#Fortran)（例如，将函数名称转换为小写或大写，通常附加下划线），因此要调用 Fortran 函数，您必须传递与您的 Fortran 编译器遵循的规则相对应的名称修饰标识符。此外，在调用 Fortran 函数时，所有输入必须作为指向堆或栈上分配值的指针传递。这不仅适用于通常在堆上分配的数组和其他可变对象，还适用于通常在栈上分配的标量值，如整数和浮点数，这些值在使用 C 或 Julia 调用约定时通常通过寄存器传递。

[`@ccall`](@ref) 生成对库函数的调用的语法是：

```julia
  @ccall library.function_name(argvalue1::argtype1, ...)::returntype
  @ccall function_name(argvalue1::argtype1, ...)::returntype
  @ccall $function_pointer(argvalue1::argtype1, ...)::returntype
```

其中 `library` 是一个字符串常量或字面量（但请参见下面的 [Non-constant Function Specifications](@ref)）。可以省略库，此时函数名称将在当前进程中解析。此形式可用于调用 C 库函数、Julia 运行时中的函数或链接到 Julia 的应用程序中的函数。也可以指定库的完整路径。或者，`@ccall` 也可以用于调用函数指针 `$function_pointer`，例如由 `Libdl.dlsym` 返回的指针。`argtype` 对应于 C 函数签名，`argvalue` 是要传递给函数的实际参数值。

!!! note
    请参见以下内容，了解如何 [map C types to Julia types](@ref mapping-c-types-to-julia)。


作为一个完整但简单的示例，以下代码在大多数Unix派生系统上调用标准C库中的`clock`函数：

```julia-repl
julia> t = @ccall clock()::Int32
2292761

julia> typeof(t)
Int32
```

`clock` 不接受任何参数，并返回一个 `Int32`。要调用 `getenv` 函数以获取环境变量值的指针，可以像这样进行调用：

```julia-repl
julia> path = @ccall getenv("SHELL"::Cstring)::Cstring
Cstring(@0x00007fff5fbffc45)

julia> unsafe_string(path)
"/bin/bash"
```

在实践中，特别是在提供可重用功能时，通常会将 `@ccall` 的使用包装在 Julia 函数中，这些函数设置参数，然后以 C 或 Fortran 函数指定的任何方式检查错误。如果发生错误，它会作为正常的 Julia 异常抛出。这一点尤其重要，因为 C 和 Fortran API 在指示错误条件方面 notoriously inconsistent。例如，`getenv` C 库函数被包装在以下 Julia 函数中，这是 [`env.jl`](https://github.com/JuliaLang/julia/blob/master/base/env.jl) 的实际定义的简化版本：

```julia
function getenv(var::AbstractString)
    val = @ccall getenv(var::Cstring)::Cstring
    if val == C_NULL
        error("getenv: undefined variable: ", var)
    end
    return unsafe_string(val)
end
```

C `getenv` 函数通过返回 `C_NULL` 来指示错误，但其他标准 C 函数以不同的方式指示错误，包括返回 -1、0、1 和其他特殊值。如果调用者尝试获取不存在的环境变量，则此包装器会抛出一个异常以指示问题：

```julia-repl
julia> getenv("SHELL")
"/bin/bash"

julia> getenv("FOOBAR")
ERROR: getenv: undefined variable: FOOBAR
```

这是一个稍微复杂一些的示例，用于发现本地机器的主机名。

```julia
function gethostname()
    hostname = Vector{UInt8}(undef, 256) # MAXHOSTNAMELEN
    err = @ccall gethostname(hostname::Ptr{UInt8}, sizeof(hostname)::Csize_t)::Int32
    Base.systemerror("gethostname", err != 0)
    hostname[end] = 0 # ensure null-termination
    return GC.@preserve hostname unsafe_string(pointer(hostname))
end
```

这个示例首先分配一个字节数组。然后调用 C 库函数 `gethostname` 来填充数组以获取主机名。最后，它获取指向主机名缓冲区的指针，并将指针转换为 Julia 字符串，假设它是一个以 null 结尾的 C 字符串。

在 C 库中，要求调用者分配内存以传递给被调用者并填充的模式是很常见的。从 Julia 进行这样的内存分配通常是通过创建一个未初始化的数组并将其数据的指针传递给 C 函数来完成的。这就是为什么我们在这里不使用 `Cstring` 类型的原因：由于数组是未初始化的，它可能包含空字节。作为 `@ccall` 的一部分，转换为 `Cstring` 会检查是否包含空字节，因此可能会抛出转换错误。

解引用 `pointer(hostname)` 使用 `unsafe_string` 是一种不安全的操作，因为它需要访问为 `hostname` 分配的内存，而这可能在此期间被垃圾回收。宏 [`GC.@preserve`](@ref) 防止了这种情况的发生，因此可以避免访问无效的内存位置。

最后，这里是通过路径指定库的示例。我们创建一个共享库，内容如下

```c
#include <stdio.h>

void say_y(int y)
{
    printf("Hello from C: got y = %d.\n", y);
}
```

并使用 `gcc -fPIC -shared -o mylib.so mylib.c` 进行编译。然后可以通过指定（绝对）路径作为库名称来调用它：

```julia-repl
julia> @ccall "./mylib.so".say_y(5::Cint)::Cvoid
Hello from C: got y = 5.
```

## Creating C-Compatible Julia Function Pointers

可以将 Julia 函数传递给接受函数指针参数的原生 C 函数。例如，匹配以下形式的 C 原型：

```c
typedef returntype (*functiontype)(argumenttype, ...)
```

宏 [`@cfunction`](@ref) 生成一个与 C 兼容的函数指针，用于调用 Julia 函数。`4d61726b646f776e2e436f64652822222c2022406366756e6374696f6e2229_40726566` 的参数是：

1. 一个 Julia 函数
2. 函数的返回类型
3. 一个输入类型的元组，对应于函数签名

!!! note
    与 `@ccall` 一样，返回类型和输入类型必须是字面常量。


!!! note
    目前，仅支持平台默认的 C 调用约定。这意味着 `@cfunction` 生成的指针不能在 WINAPI 期望 32 位 Windows 上的 `stdcall` 函数的调用中使用，但可以在 WIN64 上使用（在 WIN64 上，`stdcall` 与 C 调用约定统一）。


!!! note
    通过 `@cfunction` 暴露的回调函数不应抛出错误，因为这将意外地将控制权返回给 Julia 运行时，并可能使程序处于未定义状态。


一个经典的例子是标准 C 库中的 `qsort` 函数，声明为：

```c
void qsort(void *base, size_t nitems, size_t size,
           int (*compare)(const void*, const void*));
```

`base` 参数是一个指向长度为 `nitems` 的数组的指针，每个元素的大小为 `size` 字节。`compare` 是一个回调函数，它接受指向两个元素 `a` 和 `b` 的指针，并返回一个整数，如果 `a` 应该出现在 `b` 之前/之后，则返回小于/大于零的值（如果允许任何顺序，则返回零）。

现在，假设我们有一个一维数组 `A` 的值在 Julia 中，我们想使用 `qsort` 函数对其进行排序（而不是使用 Julia 内置的 `sort` 函数）。在考虑调用 `qsort` 并传递参数之前，我们需要编写一个比较函数：

```jldoctest mycompare
julia> function mycompare(a, b)::Cint
           return (a < b) ? -1 : ((a > b) ? +1 : 0)
       end;
```

`qsort`期望一个返回C `int`的比较函数，因此我们将返回类型注释为`Cint`。

为了将此函数传递给 C，我们使用宏 `@cfunction` 获取它的地址：

```jldoctest mycompare
julia> mycompare_c = @cfunction(mycompare, Cint, (Ref{Cdouble}, Ref{Cdouble}));
```

[`@cfunction`](@ref) 需要三个参数：Julia 函数（`mycompare`）、返回类型（`Cint`）和输入参数类型的字面元组，在这种情况下是对一个 `Cdouble`（[`Float64`](@ref)）元素的数组进行排序。

最终对 `qsort` 的调用如下：

```jldoctest mycompare
julia> A = [1.3, -2.7, 4.4, 3.1];

julia> @ccall qsort(A::Ptr{Cdouble}, length(A)::Csize_t, sizeof(eltype(A))::Csize_t, mycompare_c::Ptr{Cvoid})::Cvoid

julia> A
4-element Vector{Float64}:
 -2.7
  1.3
  3.1
  4.4
```

如示例所示，原始的 Julia 数组 `A` 现在已被排序：`[-2.7, 1.3, 3.1, 4.4]`。请注意 Julia [takes care of converting the array to a `Ptr{Cdouble}`](@ref automatic-type-conversion)），计算元素类型的字节大小，等等。

为了好玩，尝试在 `mycompare` 中插入一行 `println("mycompare($a, $b)")`，这将使你能够看到 `qsort` 正在执行的比较（并验证它确实调用了你传递给它的 Julia 函数）。

## [Mapping C Types to Julia](@id mapping-c-types-to-julia)

在Julia中，准确匹配声明的C类型与其声明是至关重要的。不一致可能导致在一个系统上正常工作的代码在另一个系统上失败或产生不确定的结果。

请注意，在调用 C 函数的过程中没有使用任何 C 头文件：您需要确保您的 Julia 类型和调用签名准确反映 C 头文件中的内容。[2]

### [Automatic Type Conversion](@id automatic-type-conversion)

Julia 自动插入对 [`Base.cconvert`](@ref) 函数的调用，以将每个参数转换为指定类型。例如，以下调用：

```julia
@ccall "libfoo".foo(x::Int32, y::Float64)::Cvoid
```

将表现得好像是这样写的：

```julia
c_x = Base.cconvert(Int32, x)
c_y = Base.cconvert(Float64, y)
GC.@preserve c_x c_y begin
    @ccall "libfoo".foo(
        Base.unsafe_convert(Int32, c_x)::Int32,
        Base.unsafe_convert(Float64, c_y)::Float64
    )::Cvoid
end
```

[`Base.cconvert`](@ref) 通常只是调用 [`convert`](@ref)，但可以定义为返回一个更适合传递给 C 的任意新对象。这应该用于执行所有将被 C 代码访问的内存分配。例如，这用于将对象的 `Array`（例如字符串）转换为指针数组。

[`Base.unsafe_convert`](@ref) 处理转换为 [`Ptr`](@ref) 类型。它被认为是不安全的，因为将对象转换为本机指针可能会使对象从垃圾收集器中隐藏，从而导致其被过早释放。

### Type Correspondences

首先，让我们回顾一些相关的Julia类型术语：

| Syntax / Keyword        | Example                                    | Description                                                                                                                                                                                                                                                       |
|:----------------------- |:------------------------------------------ |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `mutable struct`        | `BitSet`                                   | "Leaf Type" :: A group of related data that includes a type-tag, is managed by the Julia GC, and is defined by object-identity. The type parameters of a leaf type must be fully defined (no `TypeVars` are allowed) in order for the instance to be constructed. |
| `abstract type`         | `Any`, `AbstractArray{T, N}`, `Complex{T}` | "Super Type" :: A super-type (not a leaf-type) that cannot be instantiated, but can be used to describe a group of types.                                                                                                                                         |
| `T{A}`                  | `Vector{Int}`                              | "Type Parameter" :: A specialization of a type (typically used for dispatch or storage optimization).                                                                                                                                                             |
|                         |                                            | "TypeVar" :: The `T` in the type parameter declaration is referred to as a TypeVar (short for type variable).                                                                                                                                                     |
| `primitive type`        | `Int`, `Float64`                           | "Primitive Type" :: A type with no fields, but a size. It is stored and defined by-value.                                                                                                                                                                         |
| `struct`                | `Pair{Int, Int}`                           | "Struct" :: A type with all fields defined to be constant. It is defined by-value, and may be stored with a type-tag.                                                                                                                                             |
|                         | `ComplexF64` (`isbits`)                    | "Is-Bits"   :: A `primitive type`, or a `struct` type where all fields are other `isbits` types. It is defined by-value, and is stored without a type-tag.                                                                                                        |
| `struct ...; end`       | `nothing`                                  | "Singleton" :: a Leaf Type or Struct with no fields.                                                                                                                                                                                                              |
| `(...)` or `tuple(...)` | `(1, 2, 3)`                                | "Tuple" :: an immutable data-structure similar to an anonymous struct type, or a constant array. Represented as either an array or a struct.                                                                                                                      |

### [Bits Types](@id man-bits-types)

有几种特殊类型需要注意，因为没有其他类型可以被定义为具有相同的行为：

  * `Float32`

    完全对应于 C 中的 `float` 类型（或 Fortran 中的 `REAL*4`）。
  * `Float64`

    完全对应于 C 中的 `double` 类型（或 Fortran 中的 `REAL*8`）。
  * `复数F32`

    完全对应于 C 中的 `complex float` 类型（或 Fortran 中的 `COMPLEX*8`）。
  * `复数F64`

    完全对应于 C 中的 `complex double` 类型（或 Fortran 中的 `COMPLEX*16`）。
  * `签名`

    完全对应于 C 中的 `signed` 类型注释（或 Fortran 中的任何 `INTEGER` 类型）。任何不是 [`Signed`](@ref) 的 Julia 类型都被假定为无符号。

  * `Ref{T}`

    表现得像一个 `Ptr{T}`，可以通过 Julia 垃圾回收器管理其内存。

  * `数组{T,N}`

    当一个数组作为 `Ptr{T}` 参数传递给 C 时，它不会被重新解释转换：Julia 要求数组的元素类型与 `T` 匹配，并传递第一个元素的地址。

    因此，如果一个 `Array` 包含格式错误的数据，则必须通过调用 `trunc.(Int32, A)` 明确转换。

    要将数组 `A` 作为不同类型的指针传递 *而不* 事先转换数据（例如，将 `Float64` 数组传递给一个操作未解释字节的函数），您可以将参数声明为 `Ptr{Cvoid}`。

    如果将 `Ptr{T}` 类型的数组作为 `Ptr{Ptr{T}}` 参数传递，[`Base.cconvert`](@ref) 将尝试首先制作一个以空字符结尾的数组副本，每个元素都被其 `4d61726b646f776e2e436f64652822222c2022426173652e63636f6e766572742229_40726566` 版本替换。这允许，例如，将类型为 `Vector{String}` 的 `argv` 指针数组传递给类型为 `Ptr{Ptr{Cchar}}` 的参数。

在我们当前支持的所有系统中，基本的 C/C++ 值类型可以转换为 Julia 类型，如下所示。每个 C 类型都有一个对应的 Julia 类型，其名称相同，但前面加上 C。这在编写可移植代码时可以提供帮助（并且要记住，C 中的 `int` 与 Julia 中的 `Int` 并不相同）。

**系统独立类型**

| C name                                                  | Fortran name             | Standard Julia Alias | Julia Base Type                                                                                             |
|:------------------------------------------------------- |:------------------------ |:-------------------- |:----------------------------------------------------------------------------------------------------------- |
| `unsigned char`                                         | `CHARACTER`              | `Cuchar`             | `UInt8`                                                                                                     |
| `bool` (_Bool in C99+)                                  |                          | `Cuchar`             | `UInt8`                                                                                                     |
| `short`                                                 | `INTEGER*2`, `LOGICAL*2` | `Cshort`             | `Int16`                                                                                                     |
| `unsigned short`                                        |                          | `Cushort`            | `UInt16`                                                                                                    |
| `int`, `BOOL` (C, typical)                              | `INTEGER*4`, `LOGICAL*4` | `Cint`               | `Int32`                                                                                                     |
| `unsigned int`                                          |                          | `Cuint`              | `UInt32`                                                                                                    |
| `long long`                                             | `INTEGER*8`, `LOGICAL*8` | `Clonglong`          | `Int64`                                                                                                     |
| `unsigned long long`                                    |                          | `Culonglong`         | `UInt64`                                                                                                    |
| `intmax_t`                                              |                          | `Cintmax_t`          | `Int64`                                                                                                     |
| `uintmax_t`                                             |                          | `Cuintmax_t`         | `UInt64`                                                                                                    |
| `float`                                                 | `REAL*4i`                | `Cfloat`             | `Float32`                                                                                                   |
| `double`                                                | `REAL*8`                 | `Cdouble`            | `Float64`                                                                                                   |
| `complex float`                                         | `COMPLEX*8`              | `ComplexF32`         | `Complex{Float32}`                                                                                          |
| `complex double`                                        | `COMPLEX*16`             | `ComplexF64`         | `Complex{Float64}`                                                                                          |
| `ptrdiff_t`                                             |                          | `Cptrdiff_t`         | `Int`                                                                                                       |
| `ssize_t`                                               |                          | `Cssize_t`           | `Int`                                                                                                       |
| `size_t`                                                |                          | `Csize_t`            | `UInt`                                                                                                      |
| `void`                                                  |                          |                      | `Cvoid`                                                                                                     |
| `void` and `[[noreturn]]` or `_Noreturn`                |                          |                      | `Union{}`                                                                                                   |
| `void*`                                                 |                          |                      | `Ptr{Cvoid}` (or similarly `Ref{Cvoid}`)                                                                    |
| `T*` (where T represents an appropriately defined type) |                          |                      | `Ref{T}` (T may be safely mutated only if T is an isbits type)                                              |
| `char*` (or `char[]`, e.g. a string)                    | `CHARACTER*N`            |                      | `Cstring` if null-terminated, or `Ptr{UInt8}` if not                                                        |
| `char**` (or `*char[]`)                                 |                          |                      | `Ptr{Ptr{UInt8}}`                                                                                           |
| `jl_value_t*` (any Julia Type)                          |                          |                      | `Any`                                                                                                       |
| `jl_value_t* const*` (a reference to a Julia value)     |                          |                      | `Ref{Any}` (const, since mutation would require a write barrier, which is not possible to insert correctly) |
| `va_arg`                                                |                          |                      | Not supported                                                                                               |
| `...` (variadic function specification)                 |                          |                      | `T...` (where `T` is one of the above types, when using the `ccall` function)                               |
| `...` (variadic function specification)                 |                          |                      | `; va_arg1::T, va_arg2::S, etc.` (only supported with `@ccall` macro)                                       |

[`Cstring`](@ref) 类型本质上是 `Ptr{UInt8}` 的同义词，除了在转换为 `Cstring` 时，如果 Julia 字符串包含任何嵌入的空字符，则会抛出错误（这会导致字符串在 C 例程将空字符视为终止符时被静默截断）。如果您将 `char*` 传递给一个不假定空终止的 C 例程（例如，因为您传递了显式的字符串长度），或者如果您确定您的 Julia 字符串不包含空字符并想跳过检查，则可以将 `Ptr{UInt8}` 用作参数类型。`Cstring` 也可以用作 [`ccall`](@ref) 返回类型，但在这种情况下，它显然不会引入任何额外的检查，仅仅是为了提高调用的可读性。

**系统依赖类型**

| C name          | Standard Julia Alias | Julia Base Type                              |
|:--------------- |:-------------------- |:-------------------------------------------- |
| `char`          | `Cchar`              | `Int8` (x86, x86_64), `UInt8` (powerpc, arm) |
| `long`          | `Clong`              | `Int` (UNIX), `Int32` (Windows)              |
| `unsigned long` | `Culong`             | `UInt` (UNIX), `UInt32` (Windows)            |
| `wchar_t`       | `Cwchar_t`           | `Int32` (UNIX), `UInt16` (Windows)           |

!!! note
    在调用 Fortran 时，所有输入必须通过指向堆或栈分配值的指针传递，因此上述所有类型对应关系应在其类型规范周围包含一个额外的 `Ptr{..}` 或 `Ref{..}` 包装器。


!!! warning
    对于字符串参数（`char*`），Julia 类型应为 `Cstring`（如果期望是以 null 结尾的数据），否则应为 `Ptr{Cchar}` 或 `Ptr{UInt8}`（这两种指针类型效果相同），如上所述，而不是 `String`。类似地，对于数组参数（`T[]` 或 `T*`），Julia 类型应再次为 `Ptr{T}`，而不是 `Vector{T}`。


!!! warning
    Julia的`Char`类型是32位的，这与所有平台上的宽字符类型（`wchar_t`或`wint_t`）不同。


!!! warning
    返回类型 `Union{}` 意味着该函数不会返回，即 C++11 的 `[[noreturn]]` 或 C11 的 `_Noreturn`（例如 `jl_throw` 或 `longjmp`）。不要将此用于返回无值（`void`）但确实返回的函数，对于这些函数，请使用 `Cvoid`。


!!! note
    对于 `wchar_t*` 参数，Julia 类型应为 [`Cwstring`](@ref)（如果 C 例程期望一个以 null 结尾的字符串），否则为 `Ptr{Cwchar_t}`。还要注意，Julia 中的 UTF-8 字符串数据在内部是以 null 结尾的，因此可以传递给期望以 null 结尾的数据的 C 函数，而无需进行复制（但使用 `Cwstring` 类型会导致在字符串本身包含 null 字符时抛出错误）。


!!! note
    C 函数接受 `char**` 类型的参数可以通过在 Julia 中使用 `Ptr{Ptr{UInt8}}` 类型来调用。例如，形式为：

    ```c
    int main(int argc, char **argv);
    ```

    可以通过以下Julia代码调用：

    ```julia
    argv = [ "a.out", "arg1", "arg2" ]
    @ccall main(length(argv)::Int32, argv::Ptr{Ptr{UInt8}})::Int32
    ```


!!! note
    对于接受可变长度字符串的 Fortran 函数，字符串长度作为 *隐藏参数* 提供。这些参数的类型和位置在参数列表中是特定于编译器的，编译器供应商通常默认使用 `Csize_t` 作为类型，并将隐藏参数附加在参数列表的末尾。虽然某些编译器（如 GNU）的这种行为是固定的，但其他编译器（如 Intel、PGI）*可选*地允许将隐藏参数直接放在字符参数之后。例如，形式为的 Fortran 子例程

    ```fortran
    subroutine test(str1, str2)
    character(len=*) :: str1,str2
    ```

    可以通过以下Julia代码调用，其中长度被附加。

    ```julia
    str1 = "foo"
    str2 = "bar"
    ccall(:test, Cvoid, (Ptr{UInt8}, Ptr{UInt8}, Csize_t, Csize_t),
                        str1, str2, sizeof(str1), sizeof(str2))
    ```


!!! warning
    Fortran 编译器 *可能* 还会为指针、假定形状 (`:`) 和假定大小 (`*`) 数组添加其他隐藏参数。通过使用 `ISO_C_BINDING` 并在子程序的定义中包含 `bind(c)`，可以避免这种行为，这对于可互操作的代码是强烈推荐的。在这种情况下，将不会有隐藏参数，但会牺牲一些语言特性（例如，仅允许 `character(len=1)` 传递字符串）。


!!! note
    一个声明返回 `Cvoid` 的 C 函数将在 Julia 中返回值 `nothing`。


### Struct Type Correspondences

复合类型，例如 C 中的 `struct` 或 Fortran90 中的 `TYPE`（或某些 F77 变体中的 `STRUCTURE` / `RECORD`），可以通过创建具有相同字段布局的 `struct` 定义在 Julia 中进行镜像。

当递归使用时，`isbits` 类型是内联存储的。所有其他类型则存储为指向数据的指针。在 C 中，当在另一个结构体内按值使用结构体时，务必不要尝试手动复制字段，因为这将无法保持正确的字段对齐。相反，声明一个 `isbits` 结构体类型并使用它。未命名的结构体在翻译到 Julia 时是不可能的。

打包的结构体和联合声明在Julia中不被支持。

您可以在事先知道哪个字段将具有最大大小（可能包括填充）的情况下，获得 `union` 的近似值。在将您的字段转换为 Julia 时，将 Julia 字段声明为仅该类型。

参数数组可以用 `NTuple` 表示。例如，C 语言中的结构体表示为

```c
struct B {
    int A[3];
};

b_a_2 = B.A[2];
```

可以用Julia编写为

```julia
struct B
    A::NTuple{3, Cint}
end

b_a_2 = B.A[3]  # note the difference in indexing (1-based in Julia, 0-based in C)
```

未知大小的数组（C99兼容的可变长度结构，通过 `[]` 或 `[0]` 指定）不直接支持。处理这些的最佳方法通常是直接处理字节偏移量。例如，如果一个 C 库声明了一个合适的字符串类型并返回一个指向它的指针：

```c
struct String {
    int strlen;
    char data[];
};
```

在 Julia 中，我们可以独立访问各个部分以复制该字符串：

```julia
str = from_c::Ptr{Cvoid}
len = unsafe_load(Ptr{Cint}(str))
unsafe_string(str + Core.sizeof(Cint), len)
```

### Type Parameters

`@ccall` 和 `@cfunction` 的类型参数在定义包含使用的函数时静态评估。因此，它们必须采用字面元组的形式，而不是变量，并且不能引用局部变量。

这听起来可能是一个奇怪的限制，但请记住，由于 C 不是像 Julia 这样的动态语言，它的函数只能接受具有静态已知、固定签名的参数类型。

然而，虽然类型布局必须静态已知以计算预期的 C ABI，但函数的静态参数被视为此静态环境的一部分。函数的静态参数可以作为调用签名中的类型参数，只要它们不影响类型的布局。例如，`f(x::T) where {T} = @ccall valid(x::Ptr{T})::Ptr{T}` 是有效的，因为 `Ptr` 始终是一个字大小的原始类型。但是，`g(x::T) where {T} = @ccall notvalid(x::T)::T` 是无效的，因为 `T` 的类型布局在静态时并不知道。

### SIMD Values

注意：此功能目前仅在64位x86和AArch64平台上实现。

如果一个 C/C++ 例程有一个参数或返回值是原生 SIMD 类型，则相应的 Julia 类型是一个同质元组 `VecElement`，它自然映射到 SIMD 类型。具体来说：

>   * 元组的大小必须与SIMD类型相同。例如，表示x86上`__m128`的元组必须大小为16字节。
>   * 元组的元素类型必须是 `VecElement{T}` 的实例，其中 `T` 是一个原始类型，大小为 1、2、4 或 8 字节。


例如，考虑这个使用 AVX 内在函数的 C 例程：

```c
#include <immintrin.h>

__m256 dist( __m256 a, __m256 b ) {
    return _mm256_sqrt_ps(_mm256_add_ps(_mm256_mul_ps(a, a),
                                        _mm256_mul_ps(b, b)));
}
```

以下的 Julia 代码使用 `ccall` 调用 `dist`：

```julia
const m256 = NTuple{8, VecElement{Float32}}

a = m256(ntuple(i -> VecElement(sin(Float32(i))), 8))
b = m256(ntuple(i -> VecElement(cos(Float32(i))), 8))

function call_dist(a::m256, b::m256)
    @ccall "libdist".dist(a::m256, b::m256)::m256
end

println(call_dist(a,b))
```

主机必须具备必要的 SIMD 寄存器。例如，上述代码在没有 AVX 支持的主机上将无法工作。

### Memory Ownership

**`malloc`/`free`**

内存分配和释放这样的对象必须通过调用所使用库中的适当清理例程来处理，就像在任何 C 程序中一样。不要尝试在 Julia 中释放从 C 库接收到的对象 [`Libc.free`](@ref)，因为这可能导致通过错误的库调用 `free` 函数并导致进程中止。相反（将一个在 Julia 中分配的对象传递给外部库释放）同样无效。

### When to use `T`, `Ptr{T}` and `Ref{T}`

在 Julia 代码中，包装对外部 C 例程的调用时，普通（非指针）数据应在 `@ccall` 内声明为类型 `T`，因为它们是按值传递的。对于接受指针的 C 代码，通常应使用 [`Ref{T}`](@ref) 作为输入参数的类型，允许使用指向由 Julia 或 C 管理的内存的指针，通过隐式调用 [`Base.cconvert`](@ref)。相反，C 函数返回的指针应声明为输出类型 [`Ptr{T}`](@ref)，反映出指向的内存仅由 C 管理。包含在 C 结构中的指针应在相应的 Julia 结构类型中表示为类型 `Ptr{T}` 的字段，这些结构类型旨在模仿相应 C 结构的内部结构。

在 Julia 代码中包装对外部 Fortran 例程的调用时，所有输入参数应声明为 `Ref{T}` 类型，因为 Fortran 通过指针传递所有变量到内存位置。返回类型应为 `Cvoid`，用于 Fortran 子例程，或者为 `T`，用于返回类型 `T` 的 Fortran 函数。

## Mapping C Functions to Julia

### `@ccall` / `@cfunction` argument translation guide

将 C 参数列表翻译为 Julia：

  * `T`，其中 `T` 是基本类型之一：`char`、`int`、`long`、`short`、`float`、`double`、`complex`、`enum` 或其任何 `typedef` 等价物

      * `T`，其中 `T` 是上述表格中等效的 Julia 位类型
      * 如果 `T` 是一个 `enum`，则参数类型应等同于 `Cint` 或 `Cuint`。
      * 参数值将被复制（按值传递）
  * `struct T`（包括对结构体的typedef）

      * `T`，其中 `T` 是一个 Julia 叶子类型
      * 参数值将被复制（按值传递）
  * `void*`

      * 取决于这个参数是如何使用的，首先将其翻译为预期的指针类型，然后根据本列表中剩余的规则确定Julia等效类型。
      * 这个参数可以声明为 `Ptr{Cvoid}`，如果它确实只是一个未知指针的话。
  * `jl_value_t*`

      * `任何`
      * 参数值必须是一个有效的 Julia 对象
  * `jl_value_t* const*`

      * `Ref{任何}`
      * 参数列表必须是一个有效的 Julia 对象（或 `C_NULL`）
      * 不能用作输出参数，除非用户能够单独安排对象以进行GC保留。
  * `T*`

      * `Ref{T}`，其中 `T` 是与 `T` 对应的 Julia 类型
      * 参数值将被复制，如果它是 `inlinealloc` 类型（包括 `isbits`），否则，值必须是一个有效的 Julia 对象。
  * `T (*)(...)`（例如指向函数的指针）

      * `Ptr{Cvoid}`（您可能需要显式使用 [`@cfunction`](@ref) 来创建此指针）
  * `...`（例如，变长参数）

      * [for `ccall`]: `T...`，其中 `T` 是所有剩余参数的单一 Julia 类型
      * [for `@ccall`]: `; va_arg1::T, va_arg2::S, etc`，其中 `T` 和 `S` 是 Julia 类型（即用 `;` 将常规参数与可变参数分开）
      * 当前不支持 `@cfunction`
  * `va_arg`

      * 不支持 `ccall` 或 `@cfunction`

### `@ccall` / `@cfunction` return type translation guide

将 C 返回类型转换为 Julia：

  * `空`

      * `Cvoid`（这将返回单例实例 `nothing::Cvoid`）
  * `T`，其中 `T` 是基本类型之一：`char`、`int`、`long`、`short`、`float`、`double`、`complex`、`enum` 或其任何 `typedef` 等价物。

      * `T`，其中 `T` 是上述表格中等效的 Julia 位类型
      * 如果 `T` 是一个 `enum`，则参数类型应等同于 `Cint` 或 `Cuint`。
      * 参数值将被复制（按值返回）
  * `struct T`（包括对结构体的typedef）

      * `T`，其中 `T` 是一个 Julia 叶子类型
      * 参数值将被复制（按值返回）
  * `void*`

      * 取决于这个参数是如何使用的，首先将其翻译为预期的指针类型，然后根据本列表中的其余规则确定Julia等效项。
      * 这个参数可以声明为 `Ptr{Cvoid}`，如果它确实只是一个未知指针的话。
  * `jl_value_t*`

      * `任何`
      * 参数值必须是一个有效的 Julia 对象
  * `jl_value_t**`

      * `Ptr{Any}`（`Ref{Any}` 作为返回类型是无效的）
  * `T*`

      * 如果内存已经被 Julia 拥有，或者是一个 `isbits` 类型，并且已知是非空的：

          * `Ref{T}`，其中 `T` 是与 `T` 对应的 Julia 类型
          * `Ref{Any}` 的返回类型是无效的，它应该是 `Any`（对应于 `jl_value_t*`）或 `Ptr{Any}`（对应于 `jl_value_t**`）
          * C **绝对不能** 修改通过 `Ref{T}` 返回的内存，如果 `T` 是 `isbits` 类型。
      * 如果内存由 C 拥有：

          * `Ptr{T}`，其中 `T` 是与 `T` 对应的 Julia 类型
  * `T (*)(...)`（例如，指向函数的指针）

      * `Ptr{Cvoid}` 要直接从 Julia 调用，您需要将其作为第一个参数传递给 `@ccall`。请参见 [Indirect Calls](@ref)。

### Passing Pointers for Modifying Inputs

因为 C 不支持多个返回值，C 函数通常会接受指向数据的指针，以便函数可以修改这些数据。要在 `@ccall` 中实现这一点，您需要首先将值封装在适当类型的 [`Ref{T}`](@ref) 中。当您将这个 `Ref` 对象作为参数传递时，Julia 会自动传递指向封装数据的 C 指针：

```julia
width = Ref{Cint}(0)
range = Ref{Cfloat}(0)
@ccall foo(width::Ref{Cint}, range::Ref{Cfloat})::Cvoid
```

返回时，`width` 和 `range` 的内容可以通过 `width[]` 和 `range[]` 获取（如果它们被 `foo` 修改过）；也就是说，它们像零维数组一样工作。

## C Wrapper Examples

让我们从一个简单的 C 包装器示例开始，该包装器返回一个 `Ptr` 类型：

```julia
mutable struct gsl_permutation
end

# The corresponding C signature is
#     gsl_permutation * gsl_permutation_alloc (size_t n);
function permutation_alloc(n::Integer)
    output_ptr = @ccall "libgsl".gsl_permutation_alloc(n::Csize_t)::Ptr{gsl_permutation}
    if output_ptr == C_NULL # Could not allocate memory
        throw(OutOfMemoryError())
    end
    return output_ptr
end
```

[GNU Scientific Library](https://www.gnu.org/software/gsl/)（在此假设可以通过 `:libgsl` 访问）将不透明指针 `gsl_permutation *` 定义为 C 函数 `gsl_permutation_alloc` 的返回类型。由于用户代码不需要查看 `gsl_permutation` 结构体的内部，因此相应的 Julia 包装器只需要一个新的类型声明 `gsl_permutation`，该类型没有内部字段，其唯一目的是放置在 `Ptr` 类型的类型参数中。[`ccall`](@ref) 的返回类型被声明为 `Ptr{gsl_permutation}`，因为由 `output_ptr` 控制的内存是由 C 分配和指向的。

输入 `n` 是按值传递的，因此函数的输入签名简单地声明为 `::Csize_t`，不需要任何 `Ref` 或 `Ptr`。 （如果包装器调用的是 Fortran 函数，则相应的函数输入签名将改为 `::Ref{Csize_t}`，因为 Fortran 变量是通过指针传递的。）此外，`n` 可以是任何可以转换为 `Csize_t` 整数的类型；[`ccall`](@ref) 隐式调用 [`Base.cconvert(Csize_t, n)`](@ref)。

这是一个包装相应析构函数的第二个示例：

```julia
# The corresponding C signature is
#     void gsl_permutation_free (gsl_permutation * p);
function permutation_free(p::Ptr{gsl_permutation})
    @ccall "libgsl".gsl_permutation_free(p::Ptr{gsl_permutation})::Cvoid
end
```

这是第三个传递 Julia 数组的示例：

```julia
# The corresponding C signature is
#    int gsl_sf_bessel_Jn_array (int nmin, int nmax, double x,
#                                double result_array[])
function sf_bessel_Jn_array(nmin::Integer, nmax::Integer, x::Real)
    if nmax < nmin
        throw(DomainError())
    end
    result_array = Vector{Cdouble}(undef, nmax - nmin + 1)
    errorcode = @ccall "libgsl".gsl_sf_bessel_Jn_array(
                    nmin::Cint, nmax::Cint, x::Cdouble, result_array::Ref{Cdouble})::Cint
    if errorcode != 0
        error("GSL error code $errorcode")
    end
    return result_array
end
```

C 函数 wrapped 返回一个整数错误代码；实际评估 Bessel J 函数的结果填充到 Julia 数组 `result_array` 中。该变量被声明为 `Ref{Cdouble}`，因为它的内存由 Julia 分配和管理。对 [`Base.cconvert(Ref{Cdouble}, result_array)`](@ref) 的隐式调用将 Julia 指针解包为 C 可理解的 Julia 数组数据结构。

## Fortran Wrapper Example

以下示例利用 `ccall` 调用一个通用 Fortran 库 (libBLAS) 中的函数来计算点积。请注意，这里的参数映射与上面有所不同，因为我们需要从 Julia 映射到 Fortran。在每个参数类型上，我们指定 `Ref` 或 `Ptr`。这种名称修饰约定可能特定于您的 Fortran 编译器和操作系统，并且可能没有文档说明。然而，将每个参数包装在 `Ref`（或在相应情况下使用 `Ptr`）中是 Fortran 编译器实现的一个常见要求：

```julia
function compute_dot(DX::Vector{Float64}, DY::Vector{Float64})
    @assert length(DX) == length(DY)
    n = length(DX)
    incx = incy = 1
    product = @ccall "libLAPACK".ddot(
        n::Ref{Int32}, DX::Ptr{Float64}, incx::Ref{Int32}, DY::Ptr{Float64}, incy::Ref{Int32})::Float64
    return product
end
```

## Garbage Collection Safety

在传递数据给 `@ccall` 时，最好避免使用 [`pointer`](@ref) 函数。相反，定义一个 [`Base.cconvert`](@ref) 方法，并将变量直接传递给 `@ccall`。`@ccall` 会自动安排其所有参数在调用返回之前不会被垃圾回收。如果 C API 会存储对 Julia 分配的内存的引用，在 `@ccall` 返回后，您必须确保该对象对垃圾回收器仍然可见。建议的做法是创建一个类型为 `Array{Ref,1}` 的全局变量，以在 C 库通知您完成之前保存这些值。

每当您创建指向 Julia 数据的指针时，必须确保原始数据在您使用指针期间存在。Julia 中的许多方法，例如 [`unsafe_load`](@ref) 和 [`String`](@ref) 会复制数据，而不是拥有缓冲区，因此可以安全地释放（或更改）原始数据，而不会影响 Julia。一个显著的例外是 [`unsafe_wrap`](@ref)，出于性能原因，它共享（或可以被告知拥有）底层缓冲区。

垃圾收集器不保证任何终结的顺序。也就是说，如果 `a` 包含对 `b` 的引用，并且 `a` 和 `b` 都需要进行垃圾收集，则不能保证 `b` 会在 `a` 之后被终结。如果 `a` 的正确终结依赖于 `b` 的有效性，则必须以其他方式处理。

## Non-constant Function Specifications

在某些情况下，所需库的确切名称或路径在事先并不知道，必须在运行时计算。为了处理这种情况，库组件规范可以是一个函数调用，例如 `find_blas().dgemm`。当执行 `ccall` 本身时，将执行调用表达式。然而，假设库的位置一旦确定就不会改变，因此调用的结果可以被缓存和重用。因此，表达式执行的次数是未指定的，对于多个调用返回不同的值会导致未定义的行为。

如果需要更大的灵活性，可以通过以下方式使用计算值作为函数名称，方法是通过 [`eval`](@ref) 进行分阶段：

```julia
@eval @ccall "lib".$(string("a", "b"))()::Cint
```

这个表达式使用 `string` 构造一个名称，然后将这个名称替换到一个新的 `@ccall` 表达式中，随后进行评估。请记住，`eval` 仅在顶层操作，因此在这个表达式中局部变量将不可用（除非它们的值用 `$` 替换）。出于这个原因，`eval` 通常仅用于形成顶层定义，例如在包装包含许多相似函数的库时。可以为 [`@cfunction`](@ref) 构造一个类似的示例。

然而，这样做也会非常慢并且泄漏内存，因此通常应该避免这样做，而是继续阅读。下一节讨论如何使用间接调用来有效地实现类似的效果。

## Indirect Calls

`@ccall` 的第一个参数也可以是一个在运行时求值的表达式。在这种情况下，该表达式必须求值为 `Ptr`，这将用作要调用的本地函数的地址。当第一个 `@ccall` 参数包含对非常量的引用时，例如局部变量、函数参数或非常量全局变量，就会发生这种行为。

例如，您可以通过 `dlsym` 查找该函数，然后在该会话中将其缓存到共享引用中。例如：

```julia
macro dlsym(lib, func)
    z = Ref{Ptr{Cvoid}}(C_NULL)
    quote
        let zlocal = $z[]
            if zlocal == C_NULL
                zlocal = dlsym($(esc(lib))::Ptr{Cvoid}, $(esc(func)))::Ptr{Cvoid}
                $z[] = zlocal
            end
            zlocal
        end
    end
end

mylibvar = Libdl.dlopen("mylib")
@ccall $(@dlsym(mylibvar, "myfunc"))()::Cvoid
```

## Closure cfunctions

[`@cfunction`](@ref) 的第一个参数可以用 `$` 标记，在这种情况下，返回值将是一个 `struct CFunction`，它会闭合该参数。您必须确保在所有使用它的地方之前保持该返回对象的存活。通过 [`finalizer`](@ref) 删除此引用时，cfunction 指针的内容和代码将被擦除，并在程序退出时执行。这通常不是必需的，因为 C 中没有此功能，但在处理设计不良的 API 时，这可能会很有用，因为它们没有提供单独的闭包环境参数。

```julia
function qsort(a::Vector{T}, cmp) where T
    isbits(T) || throw(ArgumentError("this method can only qsort isbits arrays"))
    callback = @cfunction $cmp Cint (Ref{T}, Ref{T})
    # Here, `callback` isa Base.CFunction, which will be converted to Ptr{Cvoid}
    # (and protected against finalization) by the ccall
    @ccall qsort(a::Ptr{T}, length(a)::Csize_t, Base.elsize(a)::Csize_t, callback::Ptr{Cvoid})
    # We could instead use:
    #    GC.@preserve callback begin
    #        use(Base.unsafe_convert(Ptr{Cvoid}, callback))
    #    end
    # if we needed to use it outside of a `ccall`
    return a
end
```

!!! note
    闭包 [`@cfunction`](@ref) 依赖于 LLVM 跳板，这在并非所有平台上都可用（例如 ARM 和 PowerPC）。


## Closing a Library

有时关闭（卸载）一个库是有用的，以便可以重新加载它。例如，在为 Julia 开发 C 代码时，可能需要编译、从 Julia 调用 C 代码，然后关闭库，进行编辑，重新编译，并加载新更改。可以选择重新启动 Julia 或使用 `Libdl` 函数显式管理库，例如：

```julia
lib = Libdl.dlopen("./my_lib.so") # Open the library explicitly.
sym = Libdl.dlsym(lib, :my_fcn)   # Get a symbol for the function to call.
@ccall $sym(...) # Use the pointer `sym` instead of the library.symbol tuple.
Libdl.dlclose(lib) # Close the library explicitly.
```

请注意，当使用 `@ccall` 进行输入时（例如，`@ccall "./my_lib.so".my_fcn(...)::Cvoid`），库会被隐式打开，并且可能不会被显式关闭。

## Variadic function calls

要调用可变参数的 C 函数，可以在参数列表中使用 `分号` 来分隔必需的参数和可变参数。下面给出了一个使用 `printf` 函数的示例：

```julia-repl
julia> @ccall printf("%s = %d\n"::Cstring ; "foo"::Cstring, foo::Cint)::Cint
foo = 3
8
```

## [`ccall` interface](@id ccall-interface)

还有另一种替代接口 `@ccall`。这个接口稍微不那么方便，但它确实允许指定一个 [calling convention](@ref calling-convention)。

[`ccall`](@ref) 的参数是：

1. 一个 `(:function, "library")` 对（最常见），

    或

    一个 `:function` 名称符号或 `"function"` 名称字符串（用于当前进程或 libc 中的符号），

    或

    一个函数指针（例如，来自 `dlsym`）。
2. 函数的返回类型
3. 一个输入类型的元组，对应于函数签名。一个常见的错误是忘记了一个参数类型的 1-元组必须以逗号结尾。
4. 要传递给函数的实际参数值（如果有的话）；每个都是一个单独的参数。

!!! note
    `(:function, "library")` 对，返回类型和输入类型必须是字面常量（即，它们不能是变量，但请参见 [Non-constant Function Specifications](@ref)）。

    剩余的参数在编译时进行评估，当包含的方法被定义时。


下面给出了宏接口和函数接口之间的翻译表。

|                                                                     `@ccall` |                                                                     `ccall` |
| ----------------------------------------------------------------------------:| ---------------------------------------------------------------------------:|
|                                                      `@ccall clock()::Int32` |                                                  `ccall(:clock, Int32, ())` |
|                                                    `@ccall f(a::Cint)::Cint` |                                               `ccall(:a, Cint, (Cint,), a)` |
|                               `@ccall "mylib".f(a::Cint, b::Cdouble)::Cvoid` |                      `ccall((:f, "mylib"), Cvoid, (Cint, Cdouble), (a, b))` |
|                                                    `@ccall $fptr.f()::Cvoid` |                                                 `ccall(fptr, f, Cvoid, ())` |
|      `@ccall printf("%s = %d\n"::Cstring ; "foo"::Cstring, foo::Cint)::Cint` |                                                             `<unavailable>` |
| `@ccall printf("%s = %s\n"::Cstring ; "2 + 2"::Cstring, "5"::Cstring)::Cint` |    `ccall(:printf, Cint, (Cstring, Cstring...), "%s = %s\n", "2 + 2", "5")` |
|                                                              `<unavailable>` | `ccall(:gethostname, stdcall, Int32, (Ptr{UInt8}, UInt32), hn, length(hn))` |

## [Calling Convention](@id calling-convention)

`ccall` 的第二个参数（紧接在返回类型之前）可以选择性地是一个调用约定说明符（`@ccall` 宏目前不支持提供调用约定）。如果没有任何说明符，则使用平台默认的 C 调用约定。其他支持的约定有：`stdcall`、`cdecl`、`fastcall` 和 `thiscall`（在 64 位 Windows 上无操作）。例如（来自 `base/libc.jl`），我们看到与上面相同的 `gethostname``ccall`，但具有 Windows 的正确签名：

```julia
hn = Vector{UInt8}(undef, 256)
err = ccall(:gethostname, stdcall, Int32, (Ptr{UInt8}, UInt32), hn, length(hn))
```

有关更多信息，请参见 [LLVM Language Reference](https://llvm.org/docs/LangRef.html#calling-conventions)。

有一个额外的特殊调用约定 [`llvmcall`](@ref Base.llvmcall)，它允许直接插入对 LLVM 内置函数的调用。这在针对不寻常的平台，如 GPGPU 时尤其有用。例如，对于 [CUDA](https://llvm.org/docs/NVPTXUsage.html)，我们需要能够读取线程索引：

```julia
ccall("llvm.nvvm.read.ptx.sreg.tid.x", llvmcall, Int32, ())
```

与任何 `ccall` 一样，准确获取参数签名至关重要。此外，请注意，没有兼容层可以确保内在函数在当前目标上是合理的并且可以正常工作，这与 `Core.Intrinsics` 所暴露的等效 Julia 函数不同。

## Accessing Global Variables

由本地库导出的全局变量可以通过名称使用 [`cglobal`](@ref) 函数进行访问。`4d61726b646f776e2e436f64652822222c202263676c6f62616c2229_40726566` 的参数是与 [`ccall`](@ref) 使用的符号规范相同，以及描述存储在变量中的值的类型：

```julia-repl
julia> cglobal((:errno, :libc), Int32)
Ptr{Int32} @0x00007f418d0816b8
```

结果是一个指针，给出了值的地址。可以通过这个指针使用 [`unsafe_load`](@ref) 和 [`unsafe_store!`](@ref) 来操作这个值。

!!! note
    这个 `errno` 符号可能在名为 "libc" 的库中找不到，因为这是您系统编译器的实现细节。通常，标准库符号应该仅通过名称访问，以允许编译器填充正确的符号。然而，示例中显示的 `errno` 符号在大多数编译器中是特殊的，因此这里看到的值可能不是您所期望或想要的。在任何支持多线程的系统上编译等效的 C 代码通常会实际调用不同的函数（通过宏预处理器重载），并可能给出与这里打印的遗留值不同的结果。


## Accessing Data through a Pointer

以下方法被描述为“安全性低”，因为错误的指针或类型声明可能导致Julia突然终止。

给定一个 `Ptr{T}`，类型 `T` 的内容通常可以通过 `unsafe_load(ptr, [index])` 从引用的内存中复制到 Julia 对象中。索引参数是可选的（默认值为 1），并遵循 Julia 的 1 基索引约定。此函数故意与 [`getindex`](@ref) 和 [`setindex!`](@ref) 的行为相似（例如 `[]` 访问语法）。

返回值将是一个新对象，初始化为包含引用内存内容的副本。引用的内存可以安全地释放或释放。

如果 `T` 是 `Any`，那么内存被假定为包含对 Julia 对象的引用（一个 `jl_value_t*`），结果将是对该对象的引用，并且该对象不会被复制。在这种情况下，您必须小心确保该对象始终对垃圾收集器可见（指针不算，但新的引用算）以确保内存不会被过早释放。请注意，如果该对象最初不是由 Julia 分配的，则新的对象将永远不会被 Julia 的垃圾收集器终结。如果 `Ptr` 本身实际上是一个 `jl_value_t*`，则可以通过 [`unsafe_pointer_to_objref(ptr)`](@ref) 转换回 Julia 对象引用。（Julia 值 `v` 可以通过调用 [`pointer_from_objref(v)`](@ref) 转换为 `jl_value_t*` 指针，作为 `Ptr{Cvoid}`。）

反向操作（将数据写入 `Ptr{T}`）可以使用 [`unsafe_store!(ptr, value, [index])`](@ref) 来执行。目前，这仅支持原始类型或其他无指针（`isbits`）的不可变结构类型。

任何抛出错误的操作可能当前未实现，应作为错误报告，以便解决。

如果感兴趣的指针是一个普通数据数组（原始类型或不可变结构），函数 [`unsafe_wrap(Array, ptr,dims, own = false)`](@ref) 可能更有用。最后一个参数应该为 true，如果 Julia 应该“拥有”底层缓冲区，并在返回的 `Array` 对象被终结时调用 `free(ptr)`。如果省略 `own` 参数或为 false，调用者必须确保缓冲区在所有访问完成之前保持存在。

在Julia中，`Ptr`类型的算术运算（例如使用`+`）与C的指针算术运算并不相同。将一个整数加到`Ptr`上时，Julia总是按字节而不是元素移动指针。因此，从指针算术中获得的地址值不依赖于指针的元素类型。

## Thread-safety

一些 C 库从不同的线程执行它们的回调，由于 Julia 不是线程安全的，您需要采取一些额外的预防措施。特别是，您需要建立一个两层系统：C 回调应该仅仅 *调度*（通过 Julia 的事件循环）您的“真实”回调的执行。为此，创建一个 [`AsyncCondition`](@ref Base.AsyncCondition) 对象并在其上 [`wait`](@ref)：

```julia
cond = Base.AsyncCondition()
wait(cond)
```

您传递给 C 的回调只应执行一个 [`ccall`](@ref) 到 `:uv_async_send`，将 `cond.handle` 作为参数传递，注意避免任何分配或与 Julia 运行时的其他交互。

请注意，事件可能会合并，因此对 `uv_async_send` 的多次调用可能会导致对条件的单次唤醒通知。

## More About Callbacks

有关如何将回调传递给 C 库的更多详细信息，请参见此 [blog post](https://julialang.org/blog/2013/05/callback)。

## C++

有关创建 C++ 绑定的工具，请参阅 [CxxWrap](https://github.com/JuliaInterop/CxxWrap.jl) 包。

[^1]: Non-library function calls in both C and Julia can be inlined and thus may have even less overhead than calls to shared library functions. The point above is that the cost of actually doing foreign function call is about the same as doing a call in either native language.

[^2]: The [Clang package](https://github.com/ihnorton/Clang.jl) can be used to auto-generate Julia code from a C header file.
