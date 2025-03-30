# [Performance Tips](@id man-performance-tips)

在接下来的部分中，我们将简要介绍一些可以帮助您的 Julia 代码尽可能快速运行的技术。

## Performance critical code should be inside a function

任何对性能至关重要的代码都应该放在一个函数内。由于Julia编译器的工作方式，函数内部的代码往往比顶层代码运行得更快。

函数的使用不仅对性能重要：函数更具可重用性和可测试性，并且明确了正在执行的步骤及其输入和输出，[Write functions, not just scripts](@ref) 也是朱莉亚风格指南的一个建议。

函数应该接受参数，而不是直接操作全局变量，请参见下一点。

## Avoid untyped global variables

未类型化的全局变量的值可能在任何时刻发生变化，这可能导致其类型的变化。这使得编译器在优化使用全局变量的代码时变得困难。这同样适用于类型值变量，即全局级别的类型别名。变量应该是局部的，或者在可能的情况下作为参数传递给函数。

我们发现全局名称通常是常量，将它们声明为常量可以大大提高性能：

```julia
const DEFAULT_VAL = 0
```

如果一个全局变量被知道总是属于同一种类型，[the type should be annotated](@ref man-typed-globals)。

未类型全局变量的使用可以通过在使用点注释其类型来进行优化：

```julia
global x = rand(1000)

function loop_over_global()
    s = 0.0
    for i in x::Vector{Float64}
        s += i
    end
    return s
end
```

将参数传递给函数是一种更好的风格。这会导致代码更具可重用性，并明确输入和输出是什么。

!!! note
    在 REPL 中的所有代码都在全局作用域中评估，因此在顶层定义和赋值的变量将是一个 **全局** 变量。在模块内部的顶层作用域中定义的变量也是全局的。


在以下的 REPL 会话中：

```julia-repl
julia> x = 1.0
```

等价于：

```julia-repl
julia> global x = 1.0
```

因此之前讨论的所有性能问题都适用。

## Measure performance with [`@time`](@ref) and pay attention to memory allocation

一个用于测量性能的有用工具是 [`@time`](@ref) 宏。我们在这里重复上面的全局变量示例，但这次去掉了类型注释：

```jldoctest; setup = :(using Random; Random.seed!(1234)), filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(1000);

julia> function sum_global()
           s = 0.0
           for i in x
               s += i
           end
           return s
       end;

julia> @time sum_global()
  0.011539 seconds (9.08 k allocations: 373.386 KiB, 98.69% compilation time)
523.0007221951678

julia> @time sum_global()
  0.000091 seconds (3.49 k allocations: 70.156 KiB)
523.0007221951678
```

在第一次调用（`@time sum_global()`）时，函数会被编译。（如果您在此会话中尚未使用 [`@time`](@ref)，它还会编译计时所需的函数。）您不应该认真对待此运行的结果。对于第二次运行，请注意，除了报告时间外，它还表示分配了大量内存。我们这里只是在计算一个64位浮点数向量中所有元素的总和，因此不应该需要分配（堆）内存。

我们应该澄清的是，`@time` 报告的具体是 *堆* 分配，这通常是为了可变对象或创建/扩展可变大小的容器（例如 `Array` 或 `Dict`、字符串，或在运行时才知道类型的“类型不稳定”对象）所需。 分配（或释放）这样的内存块可能需要对 libc 进行昂贵的函数调用（例如通过 C 中的 `malloc`），并且它们必须被跟踪以进行垃圾回收。 相比之下，像数字（除了大数字）、元组和不可变 `struct` 这样的不可变值可以以更便宜的方式存储，例如在栈或 CPU 寄存器内存中，因此通常不需要担心“分配”它们的性能成本。

意外的内存分配几乎总是代码存在某种问题的迹象，通常是类型稳定性问题或创建许多小的临时数组。因此，除了分配本身之外，您函数生成的代码很可能远非最佳。认真对待这些迹象，并遵循以下建议。

在这种特定情况下，内存分配是由于使用了类型不稳定的全局变量 `x`，因此如果我们将 `x` 作为参数传递给函数，它将不再分配内存（下面报告的剩余分配是由于在全局作用域中运行 `@time` 宏所致），并且在第一次调用后速度显著更快：

```jldoctest sumarg; setup = :(using Random; Random.seed!(1234)), filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(1000);

julia> function sum_arg(x)
           s = 0.0
           for i in x
               s += i
           end
           return s
       end;

julia> @time sum_arg(x)
  0.007551 seconds (3.98 k allocations: 200.548 KiB, 99.77% compilation time)
523.0007221951678

julia> @time sum_arg(x)
  0.000006 seconds (1 allocation: 16 bytes)
523.0007221951678
```

在全局范围内运行 `@time` 宏时看到的 1 次分配。如果我们改为在一个函数中运行计时，我们可以看到确实没有进行任何分配：

```jldoctest sumarg; filter = r"[0-9\.]+ seconds"
julia> time_sum(x) = @time sum_arg(x);

julia> time_sum(x)
  0.000002 seconds
523.0007221951678
```

在某些情况下，您的函数可能需要分配内存作为其操作的一部分，这可能会使上述简单的情况变得复杂。在这种情况下，请考虑使用下面的 [tools](@ref tools) 来诊断问题，或者编写一个将分配与其算法方面分开的函数版本（请参见 [Pre-allocating outputs](@ref)）。

!!! note
    对于更严肃的基准测试，请考虑 [BenchmarkTools.jl](https://github.com/JuliaCI/BenchmarkTools.jl) 包，该包在其他方面还多次评估函数以减少噪声。


## [Tools](@id tools)

Julia及其包生态系统包括一些工具，可以帮助您诊断问题并提高代码的性能：

  * [Profiling](@ref) 允许您测量运行代码的性能并识别作为瓶颈的代码行。对于复杂项目，[ProfileView](https://github.com/timholy/ProfileView.jl) 包可以帮助您可视化您的分析结果。
  * [JET](https://github.com/aviatesk/JET.jl) 包可以帮助您找到代码中的常见性能问题。
  * 意外的大量内存分配——如 [`@time`](@ref)、[`@allocated`](@ref) 或者通过调用垃圾收集例程的分析器——暗示您的代码可能存在问题。如果您没有看到其他分配原因，请怀疑类型问题。您还可以使用 `--track-allocation=user` 选项启动 Julia，并检查生成的 `*.mem` 文件，以查看这些分配发生的位置的信息。请参见 [Memory allocation analysis](@ref)。
  * `@code_warntype` 生成了您代码的表示，这对于查找导致类型不确定性的表达式非常有帮助。请参见下面的 [`@code_warntype`](@ref)。

## [Avoid containers with abstract type parameters](@id man-performance-abstract-container)

在使用参数化类型（包括数组）时，最好尽量避免使用抽象类型进行参数化。

请考虑以下内容：

```jldoctest
julia> a = Real[]
Real[]

julia> push!(a, 1); push!(a, 2.0); push!(a, π)
3-element Vector{Real}:
 1
 2.0
 π = 3.1415926535897...
```

因为 `a` 是抽象类型 [`Real`](@ref) 的数组，它必须能够容纳任何 `Real` 值。由于 `Real` 对象可以具有任意大小和结构，因此 `a` 必须表示为指向单独分配的 `Real` 对象的指针数组。然而，如果我们只允许存储相同类型的数字，例如 [`Float64`](@ref)，那么这些可以更高效地存储：

```jldoctest
julia> a = Float64[]
Float64[]

julia> push!(a, 1); push!(a, 2.0); push!(a,  π)
3-element Vector{Float64}:
 1.0
 2.0
 3.141592653589793
```

将数字赋值给 `a` 现在会将它们转换为 `Float64`，并且 `a` 将作为一个连续的 64 位浮点值块存储，可以高效地进行操作。

如果您无法避免使用具有抽象值类型的容器，有时最好使用 `Any` 进行参数化，以避免运行时类型检查。例如，`IdDict{Any, Any}` 的性能优于 `IdDict{Type, Vector}`。

另请参阅 [Parametric Types](@ref) 下的讨论。

## Type declarations

在许多具有可选类型声明的语言中，添加声明是使代码运行更快的主要方法。但在 Julia 中情况并非如此。在 Julia 中，编译器通常知道所有函数参数、局部变量和表达式的类型。然而，在一些特定情况下，声明是有帮助的。

### Avoid fields with abstract type

类型可以在不指定其字段类型的情况下声明：

```jldoctest myambig
julia> struct MyAmbiguousType
           a
       end
```

这允许 `a` 是任何类型。这通常是有用的，但也有一个缺点：对于类型为 `MyAmbiguousType` 的对象，编译器将无法生成高性能代码。原因是编译器使用对象的类型，而不是它们的值，来确定如何构建代码。不幸的是，对于类型为 `MyAmbiguousType` 的对象，几乎无法推断出任何信息：

```jldoctest myambig
julia> b = MyAmbiguousType("Hello")
MyAmbiguousType("Hello")

julia> c = MyAmbiguousType(17)
MyAmbiguousType(17)

julia> typeof(b)
MyAmbiguousType

julia> typeof(c)
MyAmbiguousType
```

`b` 和 `c` 的值具有相同的类型，但它们在内存中的底层数据表示却非常不同。即使你在字段 `a` 中仅存储数字值，[`UInt8`](@ref) 的内存表示与 [`Float64`](@ref) 的不同，也意味着 CPU 需要使用两种不同类型的指令来处理它们。由于所需的信息在类型中不可用，因此这些决策必须在运行时做出。这会降低性能。

您可以通过声明 `a` 的类型来做得更好。在这里，我们关注的是 `a` 可能是几种类型中的任何一种的情况，在这种情况下，自然的解决方案是使用参数。例如：

```jldoctest myambig2
julia> mutable struct MyType{T<:AbstractFloat}
           a::T
       end
```

这是一个比...更好的选择

```jldoctest myambig2
julia> mutable struct MyStillAmbiguousType
           a::AbstractFloat
       end
```

因为第一个版本从包装对象的类型中指定了 `a` 的类型。例如：

```jldoctest myambig2
julia> m = MyType(3.2)
MyType{Float64}(3.2)

julia> t = MyStillAmbiguousType(3.2)
MyStillAmbiguousType(3.2)

julia> typeof(m)
MyType{Float64}

julia> typeof(t)
MyStillAmbiguousType
```

字段 `a` 的类型可以从 `m` 的类型中轻松确定，但不能从 `t` 的类型中确定。实际上，在 `t` 中可以更改字段 `a` 的类型：

```jldoctest myambig2
julia> typeof(t.a)
Float64

julia> t.a = 4.5f0
4.5f0

julia> typeof(t.a)
Float32
```

相反，一旦 `m` 被构造，`m.a` 的类型就不能改变：

```jldoctest myambig2
julia> m.a = 4.5f0
4.5f0

julia> typeof(m.a)
Float64
```

`m`的类型已知的事实——加上它的类型在函数中不能改变——使得编译器能够为像`m`这样的对象生成高度优化的代码，但不能为像`t`这样的对象生成。

当然，所有这些只有在我们用具体类型构造 `m` 的情况下才成立。我们可以通过显式地用抽象类型构造它来打破这一点：

```jldoctest myambig2
julia> m = MyType{AbstractFloat}(3.2)
MyType{AbstractFloat}(3.2)

julia> typeof(m.a)
Float64

julia> m.a = 4.5f0
4.5f0

julia> typeof(m.a)
Float32
```

对于所有实际目的，这些对象的行为与 `MyStillAmbiguousType` 的对象完全相同。

比较为一个简单函数生成的代码量是非常有启发性的。

```julia
func(m::MyType) = m.a+1
```

使用

```julia
code_llvm(func, Tuple{MyType{Float64}})
code_llvm(func, Tuple{MyType{AbstractFloat}})
```

由于篇幅原因，这里不显示结果，但您可能希望自己尝试一下。因为在第一种情况下类型是完全指定的，编译器不需要生成任何代码来在运行时解析类型。这导致了更短和更快的代码。

一个人还应该记住，未完全参数化的类型表现得像抽象类型。例如，尽管完全指定的 `Array{T,n}` 是具体的，但没有给出参数的 `Array` 本身并不是具体的：

```jldoctest myambig3
julia> !isconcretetype(Array), !isabstracttype(Array), isstructtype(Array), !isconcretetype(Array{Int}), isconcretetype(Array{Int,1})
(true, true, true, true, true)
```

在这种情况下，最好避免将 `MyType` 声明为具有字段 `a::Array`，而是将字段声明为 `a::Array{T,N}` 或 `a::A`，其中 `{T,N}` 或 `A` 是 `MyType` 的参数。

之前的建议在结构体的字段旨在成为函数或更一般的可调用对象时尤其有用。定义一个结构体如下是非常诱人的：

```julia
struct MyCallableWrapper
    f::Function
end
```

但是由于 `Function` 是一个抽象类型，对 `wrapper.f` 的每次调用都将需要动态分发，因为访问字段 `f` 的类型不稳定。相反，您应该写一些类似于：

```julia
struct MyCallableWrapper{F}
    f::F
end
```

其行为几乎完全相同，但速度会更快（因为类型不稳定性被消除）。请注意，我们不强加 `F<:Function`：这意味着不属于 `Function` 的可调用对象也被允许用于字段 `f`。

### Avoid fields with abstract containers

相同的最佳实践也适用于容器类型：

```jldoctest containers
julia> struct MySimpleContainer{A<:AbstractVector}
           a::A
       end

julia> struct MyAmbiguousContainer{T}
           a::AbstractVector{T}
       end

julia> struct MyAlsoAmbiguousContainer
           a::Array
       end
```

例如：

```jldoctest containers
julia> c = MySimpleContainer(1:3);

julia> typeof(c)
MySimpleContainer{UnitRange{Int64}}

julia> c = MySimpleContainer([1:3;]);

julia> typeof(c)
MySimpleContainer{Vector{Int64}}

julia> b = MyAmbiguousContainer(1:3);

julia> typeof(b)
MyAmbiguousContainer{Int64}

julia> b = MyAmbiguousContainer([1:3;]);

julia> typeof(b)
MyAmbiguousContainer{Int64}

julia> d = MyAlsoAmbiguousContainer(1:3);

julia> typeof(d), typeof(d.a)
(MyAlsoAmbiguousContainer, Vector{Int64})

julia> d = MyAlsoAmbiguousContainer(1:1.0:3);

julia> typeof(d), typeof(d.a)
(MyAlsoAmbiguousContainer, Vector{Float64})

```

对于 `MySimpleContainer`，对象由其类型和参数完全指定，因此编译器可以生成优化的函数。在大多数情况下，这可能就足够了。

虽然编译器现在可以很好地完成它的工作，但在某些情况下，*你* 可能希望你的代码能够根据 `a` 的 *元素类型* 执行不同的操作。通常，实现这一目标的最佳方法是将你的特定操作（在这里是 `foo`）封装在一个单独的函数中：

```jldoctest containers
julia> function sumfoo(c::MySimpleContainer)
           s = 0
           for x in c.a
               s += foo(x)
           end
           s
       end
sumfoo (generic function with 1 method)

julia> foo(x::Integer) = x
foo (generic function with 1 method)

julia> foo(x::AbstractFloat) = round(x)
foo (generic function with 2 methods)
```

这使事情变得简单，同时允许编译器在所有情况下生成优化的代码。

然而，在某些情况下，您可能需要为 `MySimpleContainer` 中字段 `a` 的不同元素类型或 `AbstractVector` 的不同类型声明外部函数的不同版本。您可以这样做：

```jldoctest containers
julia> function myfunc(c::MySimpleContainer{<:AbstractArray{<:Integer}})
           return c.a[1]+1
       end
myfunc (generic function with 1 method)

julia> function myfunc(c::MySimpleContainer{<:AbstractArray{<:AbstractFloat}})
           return c.a[1]+2
       end
myfunc (generic function with 2 methods)

julia> function myfunc(c::MySimpleContainer{Vector{T}}) where T <: Integer
           return c.a[1]+3
       end
myfunc (generic function with 3 methods)
```

```jldoctest containers
julia> myfunc(MySimpleContainer(1:3))
2

julia> myfunc(MySimpleContainer(1.0:3))
3.0

julia> myfunc(MySimpleContainer([1:3;]))
4
```

### Annotate values taken from untyped locations

通常，使用可能包含任何类型值的数据结构（如 `Array{Any}` 数组）是很方便的。但是，如果您正在使用这些结构之一并且恰好知道某个元素的类型，那么将此信息与编译器共享是有帮助的：

```julia
function foo(a::Array{Any,1})
    x = a[1]::Int32
    b = x+1
    ...
end
```

在这里，我们恰好知道 `a` 的第一个元素将是 [`Int32`](@ref)。像这样添加注释的好处在于，如果值不是预期的类型，它将引发运行时错误，从而可能更早地捕捉到某些错误。

在`a[1]`的类型不明确的情况下，可以通过`x = convert(Int32, a[1])::Int32`来声明`x`。使用[`convert`](@ref)函数允许`a[1]`是任何可以转换为`Int32`的对象（例如`UInt8`），从而通过放宽类型要求来增加代码的通用性。请注意，在这种情况下，`convert`本身需要类型注释以实现类型稳定性。这是因为编译器无法推断函数的返回值类型，即使是`convert`，除非所有函数参数的类型都是已知的。

类型注解不会增强（实际上可能会妨碍）性能，如果类型是抽象的或在运行时构造的。这是因为编译器无法利用注解来专门化后续代码，并且类型检查本身也需要时间。例如，在代码中：

```julia
function nr(a, prec)
    ctype = prec == 32 ? Float32 : Float64
    b = Complex{ctype}(a)
    c = (b + 1.0f0)::Complex{ctype}
    abs(c)
end
```

`c` 的注解会影响性能。要编写涉及运行时构造类型的高性能代码，请使用下面讨论的 [function-barrier technique](@ref kernel-functions)，并确保构造的类型出现在内核函数的参数类型中，以便编译器能够正确地对内核操作进行特化。例如，在上面的代码片段中，一旦 `b` 被构造，就可以将其传递给另一个函数 `k`，即内核。如果，例如，函数 `k` 将 `b` 声明为类型 `Complex{T}` 的参数，其中 `T` 是类型参数，那么在 `k` 中的赋值语句中出现的类型注解形式为：

```julia
c = (b + 1.0f0)::Complex{T}
```

不会影响性能（但也没有帮助），因为编译器可以在编译 `k` 时确定 `c` 的类型。

### Be aware of when Julia avoids specializing

作为一种启发式方法，Julia 在三种特定情况下避免自动 [specializing](@ref man-method-specializations) 参数类型：`Type`、`Function` 和 `Vararg`。当参数在方法中使用时，Julia 总是会进行特化，但如果参数只是传递给另一个函数，则不会。这通常在运行时对性能没有影响，并且 [improves compiler performance](@ref compiler-efficiency-issues)。如果您发现它在您的情况下确实对运行时性能有影响，您可以通过在方法声明中添加类型参数来触发特化。以下是一些示例：

这将不会专业化：

```julia
function f_type(t)  # or t::Type
    x = ones(t, 10)
    return sum(map(sin, x))
end
```

但这将：

```julia
function g_type(t::Type{T}) where T
    x = ones(T, 10)
    return sum(map(sin, x))
end
```

这些将不会专业化：

```julia
f_func(f, num) = ntuple(f, div(num, 2))
g_func(g::Function, num) = ntuple(g, div(num, 2))
```

但这将：

```julia
h_func(h::H, num) where {H} = ntuple(h, div(num, 2))
```

这不会专业化：

```julia
f_vararg(x::Int...) = tuple(x...)
```

但这将：

```julia
g_vararg(x::Vararg{Int, N}) where {N} = tuple(x...)
```

只需引入一个类型参数即可强制特化，即使其他类型没有约束。例如，这也会进行特化，并且在参数不全为相同类型时非常有用：

```julia
h_vararg(x::Vararg{Any, N}) where {N} = tuple(x...)
```

注意，[`@code_typed`](@ref) 和朋友们将始终向你展示专门的代码，即使Julia通常不会专门化该方法调用。你需要检查 [method internals](@ref ast-lowered-method)，如果你想查看在参数类型更改时是否生成了专门化，即，如果 `Base.specializations(@which f(...))` 包含相关参数的专门化。

## Break functions into multiple definitions

将函数写成多个小定义允许编译器直接调用最适用的代码，甚至将其内联。

这是一个“复合函数”的示例，实际上应该写成多个定义：

```julia
using LinearAlgebra

function mynorm(A)
    if isa(A, Vector)
        return sqrt(real(dot(A,A)))
    elseif isa(A, Matrix)
        return maximum(svdvals(A))
    else
        error("mynorm: invalid argument")
    end
end
```

这可以更简洁高效地写成：

```julia
mynorm(x::Vector) = sqrt(real(dot(x, x)))
mynorm(A::Matrix) = maximum(svdvals(A))
```

然而，应该注意的是，编译器在优化掉像 `mynorm` 示例中编写的代码中的无效分支方面非常高效。

## Write "type-stable" functions

当可能时，确保一个函数始终返回相同类型的值是有帮助的。考虑以下定义：

```julia
pos(x) = x < 0 ? 0 : x
```

虽然这看起来无害，但问题在于 `0` 是一个整数（类型为 `Int`），而 `x` 可能是任何类型。因此，根据 `x` 的值，这个函数可能返回两种类型中的任意一种。这种行为是允许的，在某些情况下可能是可取的。但可以很容易地通过以下方式修复：

```julia
pos(x) = x < 0 ? zero(x) : x
```

还有一个 [`oneunit`](@ref) 函数，以及一个更通用的 [`oftype(x, y)`](@ref) 函数，它将 `y` 转换为 `x` 的类型。

## Avoid changing the type of a variable

在函数中反复使用的变量存在类似的“类型稳定性”问题：

```julia
function foo()
    x = 1
    for i = 1:10
        x /= rand()
    end
    return x
end
```

局部变量 `x` 最初是一个整数，在一次循环迭代后变成了一个浮点数（[`/`](@ref) 运算符的结果）。这使得编译器更难优化循环体。有几种可能的解决方案：

  * 初始化 `x` 为 `x = 1.0`
  * 声明 `x` 的类型为 `x::Float64 = 1`
  * 使用显式转换 `x = oneunit(Float64)`
  * 初始化第一个循环迭代，设置 `x = 1 / rand()`，然后循环 `for i = 2:10`

## [Separate kernel functions (aka, function barriers)](@id kernel-functions)

许多函数遵循一个模式，即先进行一些设置工作，然后运行多个迭代以执行核心计算。在可能的情况下，将这些核心计算放在单独的函数中是一个好主意。例如，以下这个虚构的函数返回一个随机选择类型的数组：

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> function strange_twos(n)
           a = Vector{rand(Bool) ? Int64 : Float64}(undef, n)
           for i = 1:n
               a[i] = 2
           end
           return a
       end;

julia> strange_twos(3)
3-element Vector{Int64}:
 2
 2
 2
```

请将其写为：

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> function fill_twos!(a)
           for i = eachindex(a)
               a[i] = 2
           end
       end;

julia> function strange_twos(n)
           a = Vector{rand(Bool) ? Int64 : Float64}(undef, n)
           fill_twos!(a)
           return a
       end;

julia> strange_twos(3)
3-element Vector{Int64}:
 2
 2
 2
```

Julia 的编译器在函数边界为参数类型专门化代码，因此在原始实现中，它在循环期间并不知道 `a` 的类型（因为它是随机选择的）。因此，第二个版本通常更快，因为内部循环可以作为 `fill_twos!` 的一部分针对不同类型的 `a` 进行重新编译。

第二种形式通常也是更好的风格，并且可以导致更多的代码重用。

此模式在 Julia Base 的多个地方使用。例如，参见 `vcat` 和 `hcat` 在 [`abstractarray.jl`](https://github.com/JuliaLang/julia/blob/40fe264f4ffaa29b749bcf42239a89abdcbba846/base/abstractarray.jl#L1205-L1206)，或者 [`fill!`](@ref) 函数，我们本可以使用它而不是编写自己的 `fill_twos!`。

像 `strange_twos` 这样的函数在处理不确定类型的数据时出现，例如从输入文件加载的数据可能包含整数、浮点数、字符串或其他内容。

## [Types with values-as-parameters](@id man-performance-value-type)

假设你想创建一个在每个轴上大小为 3 的 `N` 维数组。这样的数组可以这样创建：

```jldoctest
julia> A = fill(5.0, (3, 3))
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

这种方法非常有效：编译器可以确定 `A` 是 `Array{Float64,2}`，因为它知道填充值的类型（`5.0::Float64`）和维度（`(3, 3)::NTuple{2,Int}`）。这意味着编译器可以为在同一函数中对 `A` 的任何未来使用生成非常高效的代码。

但是现在假设你想写一个函数来创建一个任意维度的 3×3×... 数组；你可能会想写一个函数

```jldoctest
julia> function array3(fillval, N)
           fill(fillval, ntuple(d->3, N))
       end
array3 (generic function with 1 method)

julia> array3(5.0, 2)
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

这可以工作，但（正如你可以通过使用 `@code_warntype array3(5.0, 2)` 自行验证的那样）问题在于输出类型无法推断：参数 `N` 是类型为 `Int` 的一个 *值*，而类型推断无法（也不可能）提前预测它的值。这意味着使用此函数输出的代码必须是保守的，在每次访问 `A` 时检查类型；这样的代码会非常慢。

现在，解决此类问题的一种非常好的方法是使用 [function-barrier technique](@ref kernel-functions)。然而，在某些情况下，您可能希望完全消除类型不稳定性。在这种情况下，一种方法是将维度作为参数传递，例如通过 `Val{T}()`（参见 ["Value types"](@ref)）：

```jldoctest
julia> function array3(fillval, ::Val{N}) where N
           fill(fillval, ntuple(d->3, Val(N)))
       end
array3 (generic function with 1 method)

julia> array3(5.0, Val(2))
3×3 Matrix{Float64}:
 5.0  5.0  5.0
 5.0  5.0  5.0
 5.0  5.0  5.0
```

Julia 有一个专门的 `ntuple` 版本，它接受 `Val{::Int}` 实例作为第二个参数；通过将 `N` 作为类型参数传递，您使其“值”对编译器可知。因此，这个版本的 `array3` 允许编译器预测返回类型。

然而，使用这些技术可能会出人意料地微妙。例如，如果你从这样的函数中调用 `array3`，那将没有任何帮助：

```julia
function call_array3(fillval, n)
    A = array3(fillval, Val(n))
end
```

在这里，你又一次创建了同样的问题：编译器无法猜测 `n` 是什么，因此它不知道 `Val(n)` 的 *类型*。尝试使用 `Val`，但错误地使用它，在许多情况下很容易导致性能 *变差*。（只有在你有效地将 `Val` 与函数障碍技巧结合使用，以使内核函数更高效的情况下，才应该使用上述代码。）

`Val` 的正确用法示例是：

```julia
function filter3(A::AbstractArray{T,N}) where {T,N}
    kernel = array3(1, Val(N))
    filter(A, kernel)
end
```

在这个例子中，`N` 被作为参数传递，因此它的“值”对编译器是已知的。基本上，`Val(T)` 仅在 `T` 是硬编码/字面量（`Val(3)`）或已经在类型域中指定时有效。

## The dangers of abusing multiple dispatch (aka, more on types with values-as-parameters)

一旦一个人学会了欣赏多重分发，就会有一种可以理解的倾向，想要过度使用它，试图将其应用于所有事情。例如，你可能会想象使用它来存储信息，例如

```
struct Car{Make, Model}
    year::Int
    ...more fields...
end
```

然后在对象上调度，例如 `Car{:Honda,:Accord}(year, args...)`。

这在以下任一情况下可能是值得的：

  * 您需要对每个 `Car` 进行 CPU 密集型处理，如果您在编译时知道 `Make` 和 `Model`，并且将使用的不同 `Make` 或 `Model` 的总数不是太大，那么效率会大大提高。
  * 您有同类的 `Car` 列表需要处理，因此您可以将它们全部存储在 `Array{Car{:Honda,:Accord},N}` 中。

当后者成立时，处理这种同质数组的函数可以有效地进行特化：Julia 事先知道每个元素的类型（容器中的所有对象具有相同的具体类型），因此 Julia 可以在函数编译时“查找”正确的方法调用（避免在运行时进行检查），从而为处理整个列表生成高效的代码。

当这些条件不成立时，您可能得不到任何好处；更糟糕的是，结果将导致“类型的组合爆炸”，这将适得其反。如果 `items[i+1]` 的类型与 `item[i]` 不同，Julia 必须在运行时查找类型，在方法表中搜索适当的方法，通过类型交集决定哪个匹配，确定它是否已经被 JIT 编译（如果没有，则进行编译），然后进行调用。实质上，您是在要求完整的类型系统和 JIT 编译机制基本上执行相当于您自己代码中的 switch 语句或字典查找。

一些运行时基准测试比较了（1）类型调度，（2）字典查找，以及（3）“switch”语句，可以在 [on the mailing list](https://groups.google.com/forum/#!msg/julia-users/jUMu9A3QKQQ/qjgVWr7vAwAJ) 找到。

或许比运行时影响更糟糕的是编译时影响：Julia 将为每个不同的 `Car{Make, Model}` 编译专门的函数；如果你有数百或数千种这样的类型，那么每个接受此类对象作为参数的函数（从你自己可能编写的自定义 `get_year` 函数，到 Julia Base 中的通用 `push!` 函数）将会为其编译数百或数千个变体。每一个变体都会增加已编译代码的缓存大小、内部方法列表的长度等。对值作为参数的过度热情很容易浪费巨大的资源。

## [Access arrays in memory order, along columns](@id man-performance-column-major)

在Julia中，多维数组以列优先顺序存储。这意味着数组是按列堆叠的。可以使用`vec`函数或语法`[:]`来验证这一点，如下所示（注意数组的顺序是`[1 3 2 4]`，而不是`[1 2 3 4]`）：

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> x[:]
4-element Vector{Int64}:
 1
 3
 2
 4
```

这种数组排序的约定在许多语言中很常见，比如 Fortran、Matlab 和 R（仅举几例）。列主序的替代方案是行主序，这是 C 和 Python（`numpy`）等其他语言采用的约定。记住数组的排序在循环遍历数组时可能会产生显著的性能影响。一个需要记住的经验法则是，对于列主序数组，第一索引变化得最快。本质上，这意味着如果内层循环索引在切片表达式中最先出现，循环将会更快。请记住，用 `:` 索引数组是一个隐式循环，它迭代访问特定维度内的所有元素；例如，提取列可能比提取行更快。

考虑以下这个人为的例子。想象一下我们想要编写一个函数，该函数接受一个 [`Vector`](@ref) 并返回一个方形 [`Matrix`](@ref)，其中行或列填充了输入向量的副本。假设填充行还是列并不重要（也许其余的代码可以相应地轻松调整）。我们可以想象至少有四种方法来实现这一点（除了推荐调用内置的 [`repeat`](@ref)）：

```julia
function copy_cols(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for i = inds
        out[:, i] = x
    end
    return out
end

function copy_rows(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for i = inds
        out[i, :] = x
    end
    return out
end

function copy_col_row(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for col = inds, row = inds
        out[row, col] = x[row]
    end
    return out
end

function copy_row_col(x::Vector{T}) where T
    inds = axes(x, 1)
    out = similar(Array{T}, inds, inds)
    for row = inds, col = inds
        out[row, col] = x[col]
    end
    return out
end
```

现在我们将使用相同的随机 `10000` x `1` 输入向量来计时每个函数：

```julia-repl
julia> x = randn(10000);

julia> fmt(f) = println(rpad(string(f)*": ", 14, ' '), @elapsed f(x))

julia> map(fmt, [copy_cols, copy_rows, copy_col_row, copy_row_col]);
copy_cols:    0.331706323
copy_rows:    1.799009911
copy_col_row: 0.415630047
copy_row_col: 1.721531501
```

注意到 `copy_cols` 比 `copy_rows` 快得多。这是可以预期的，因为 `copy_cols` 尊重 `Matrix` 的列优先内存布局，并且一次填充一列。此外，`copy_col_row` 比 `copy*row*col 快得多，因为它遵循我们的经验法则，即在切片表达式中首先出现的元素应该与最内层的循环配对。

## Pre-allocating outputs

如果您的函数返回一个 `Array` 或其他复杂类型，它可能需要分配内存。不幸的是，分配和其反向操作，即垃圾回收，往往是显著的瓶颈。

有时，您可以通过预分配输出，避免在每次函数调用时分配内存。作为一个简单的例子，比较

```jldoctest prealloc
julia> function xinc(x)
           return [x, x+1, x+2]
       end;

julia> function loopinc()
           y = 0
           for i = 1:10^7
               ret = xinc(i)
               y += ret[2]
           end
           return y
       end;
```

与

```jldoctest prealloc
julia> function xinc!(ret::AbstractVector{T}, x::T) where T
           ret[1] = x
           ret[2] = x+1
           ret[3] = x+2
           nothing
       end;

julia> function loopinc_prealloc()
           ret = Vector{Int}(undef, 3)
           y = 0
           for i = 1:10^7
               xinc!(ret, i)
               y += ret[2]
           end
           return y
       end;
```

计时结果：

```jldoctest prealloc; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> @time loopinc()
  0.529894 seconds (40.00 M allocations: 1.490 GiB, 12.14% gc time)
50000015000000

julia> @time loopinc_prealloc()
  0.030850 seconds (6 allocations: 288 bytes)
50000015000000
```

预分配还有其他优点，例如允许调用者控制算法的“输出”类型。在上面的例子中，如果我们愿意，可以传递一个 `SubArray` 而不是 [`Array`](@ref)。

在极端情况下，预分配可能会使你的代码变得更丑，因此可能需要进行性能测量和一些判断。然而，对于“向量化”（逐元素）函数，可以使用方便的语法 `x .= f.(y)` 进行就地操作，结合融合循环且不使用临时数组（参见 [dot syntax for vectorizing functions](@ref man-vectorized)）。

## [Use `MutableArithmetics` for more control over allocation for mutable arithmetic types](@id man-perftips-mutablearithmetics)

一些 [`Number`](@ref) 子类型，例如 [`BigInt`](@ref) 或 [`BigFloat`](@ref)，可以实现为 [`mutable struct`](@ref) 类型，或者它们可能具有可变组件。在这种情况下，Julia `Base` 中的算术接口通常选择便利性而非效率，因此以天真的方式使用它们可能会导致性能不佳。另一方面，[`MutableArithmetics`](https://juliahub.com/ui/Packages/General/MutableArithmetics) 包的抽象使得利用这些类型的可变性来编写仅分配必要内存的快速代码成为可能。`MutableArithmetics` 还使得在必要时可以显式复制可变算术类型的值。`MutableArithmetics` 是一个用户包，并不隶属于 Julia 项目。

## More dots: Fuse vectorized operations

Julia 有一个特殊的 [dot syntax](@ref man-vectorized)，可以将任何标量函数转换为“向量化”函数调用，并将任何运算符转换为“向量化”运算符，具有嵌套“点调用”*融合*的特殊属性：它们在语法层面上合并为一个单一的循环，而不分配临时数组。如果您使用 `.=` 和类似的赋值运算符，结果也可以直接存储在预分配的数组中（见上文）。

在线性代数的上下文中，这意味着尽管像 `vector + vector` 和 `vector * scalar` 这样的操作是定义好的，但使用 `vector .+ vector` 和 `vector .* scalar` 可能更有优势，因为生成的循环可以与周围的计算融合。例如，考虑这两个函数：

```jldoctest dotfuse
julia> f(x) = 3x.^2 + 4x + 7x.^3;

julia> fdot(x) = @. 3x^2 + 4x + 7x^3; # equivalent to 3 .* x.^2 .+ 4 .* x .+ 7 .* x.^3
```

`f` 和 `fdot` 计算的是相同的内容。然而，当应用于数组时，`fdot`（通过 [`@.`](@ref @__dot__) 宏定义）显著更快：

```jldoctest dotfuse; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> x = rand(10^6);

julia> @time f(x);
  0.019049 seconds (16 allocations: 45.777 MiB, 18.59% gc time)

julia> @time fdot(x);
  0.002790 seconds (6 allocations: 7.630 MiB)

julia> @time f.(x);
  0.002626 seconds (8 allocations: 7.630 MiB)
```

也就是说，`fdot(x)` 的速度是 `f(x)` 的十倍，并且分配的内存是 `f(x)` 的 1/6，因为 `f(x)` 中的每个 `*` 和 `+` 操作都会分配一个新的临时数组，并在一个单独的循环中执行。在这个例子中，`f.(x)` 的速度与 `fdot(x)` 一样快，但在许多情况下，在表达式中添加一些点比为每个向量化操作定义一个单独的函数更方便。

## [Fewer dots: Unfuse certain intermediate broadcasts](@id man-performance-unfuse)

上述提到的点循环融合使得简洁且符合习惯的代码能够表达高性能的操作。然而，重要的是要记住，融合的操作将在广播的每次迭代中计算。这意味着在某些情况下，特别是在存在复合或多维广播的情况下，带有点调用的表达式可能会计算一个函数的次数超过预期。例如，假设我们想构建一个随机矩阵，其行的欧几里得范数为1。我们可能会写如下内容：

```
julia> x = rand(1000, 1000);

julia> d = sum(abs2, x; dims=2);

julia> @time x ./= sqrt.(d);
  0.002049 seconds (4 allocations: 96 bytes)
```

这将有效。然而，这个表达式实际上会对行 `x[i, :]` 中的 *每个* 元素重新计算 `sqrt(d[i])`，这意味着计算的平方根数量远远超过所需。为了准确查看广播将在哪些索引上迭代，我们可以在融合表达式的参数上调用 `Broadcast.combine_axes`。这将返回一个范围的元组，其条目对应于迭代的轴；这些范围的长度的乘积将是对融合操作的总调用次数。

因此，当广播表达式的某些组件在某个轴上是常量时——就像前面示例中第二维度上的 `sqrt`——通过强制“解融合”这些组件，有可能提高性能，即提前分配广播操作的结果并沿其常量轴重用缓存值。一些这样的潜在方法是使用临时变量，将点表达式的组件包装在 `identity` 中，或使用等效的内在向量化（但非融合）函数。

```
julia> @time let s = sqrt.(d); x ./= s end;
  0.000809 seconds (5 allocations: 8.031 KiB)

julia> @time x ./= identity(sqrt.(d));
  0.000608 seconds (5 allocations: 8.031 KiB)

julia> @time x ./= map(sqrt, d);
  0.000611 seconds (4 allocations: 8.016 KiB)
```

这些选项中的任何一个都可以在分配的代价下实现大约三倍的加速；对于大型可广播对象，这种加速可以在渐近上非常大。

## [Consider using views for slices](@id man-performance-views)

在 Julia 中，数组 "切片" 表达式如 `array[1:5, :]` 会创建该数据的副本（除了在赋值的左侧，`array[1:5, :] = ...` 会就地赋值到 `array` 的那部分）。如果你在切片上进行许多操作，这对性能是有好处的，因为处理一个较小的连续副本比索引原始数组更高效。另一方面，如果你只是对切片进行一些简单的操作，分配和复制操作的成本可能会很高。

一种替代方法是创建一个数组的“视图”，这是一个数组对象（`SubArray`），它实际上引用了原始数组的数据，而不进行复制。（如果你对视图进行写操作，它也会修改原始数组的数据。）可以通过调用 [`view`](@ref) 来为单个切片完成此操作，或者更简单地通过在整个表达式或代码块前放置 [`@views`](@ref) 来完成。例如：

```jldoctest; filter = r"[0-9\.]+ seconds \(.*?\)"
julia> fcopy(x) = sum(x[2:end-1]);

julia> @views fview(x) = sum(x[2:end-1]);

julia> x = rand(10^6);

julia> @time fcopy(x);
  0.003051 seconds (3 allocations: 7.629 MB)

julia> @time fview(x);
  0.001020 seconds (1 allocation: 16 bytes)
```

注意到 `fview` 版本的函数不仅实现了 3 倍的加速，还减少了内存分配。

## Copying data is not always bad

数组在内存中是连续存储的，这使得它们适合CPU向量化，并由于缓存的原因减少内存访问。这些也是推荐以列优先顺序访问数组的原因（见上文）。不规则的访问模式和非连续视图会因为非顺序内存访问而显著减慢数组上的计算。

在重复访问之前，将不规则访问的数据复制到一个连续的数组中可以带来显著的速度提升，如下面的例子所示。在这里，一个矩阵在随机打乱的索引处被访问，然后进行乘法运算。即使考虑到复制和分配的额外成本，将数据复制到普通数组中也能加速乘法运算。

```julia-repl
julia> using Random

julia> A = randn(3000, 3000);

julia> x = randn(2000);

julia> inds = shuffle(1:3000)[1:2000];

julia> function iterated_neural_network(A, x, depth)
           for _ in 1:depth
               x .= max.(0, A * x)
           end
           argmax(x)
       end

julia> @time iterated_neural_network(view(A, inds, inds), x, 10)
  0.324903 seconds (12 allocations: 157.562 KiB)
1569

julia> @time iterated_neural_network(A[inds, inds], x, 10)
  0.054576 seconds (13 allocations: 30.671 MiB, 13.33% gc time)
1569
```

只要有足够的内存，将视图复制到数组的成本就会被在连续数组上进行重复矩阵乘法所带来的速度提升所抵消。

## Consider StaticArrays.jl for small fixed-size vector/matrix operations

如果您的应用涉及许多小的（`< 100` 元素）固定大小的数组（即大小在执行之前已知），那么您可能想考虑使用 [StaticArrays.jl package](https://github.com/JuliaArrays/StaticArrays.jl)。该包允许您以一种避免不必要的堆分配的方式表示这些数组，并允许编译器针对数组的 *大小* 专门化代码，例如通过完全展开向量操作（消除循环）并将元素存储在 CPU 寄存器中。

例如，如果您正在进行二维几何的计算，您可能会有许多与2组件向量的计算。通过使用StaticArrays.jl中的`SVector`类型，您可以使用方便的向量表示法和操作，例如在向量`v`和`w`上使用`norm(3v - w)`，同时允许编译器展开代码，以实现与`@inbounds hypot(3v[1]-w[1], 3v[2]-w[2])`等效的最小计算。

## Avoid string interpolation for I/O

在将数据写入文件（或其他 I/O 设备）时，形成额外的中间字符串是一个开销来源。与其：

```julia
println(file, "$a $b")
```

使用：

```julia
println(file, a, " ", b)
```

代码的第一个版本形成一个字符串，然后将其写入文件，而第二个版本则直接将值写入文件。还要注意，在某些情况下，字符串插值可能更难以阅读。考虑：

```julia
println(file, "$(f(a))$(f(b))")
```

对抗：

```julia
println(file, f(a), f(b))
```

## Optimize network I/O during parallel execution

当并行执行远程函数时：

```julia
using Distributed

responses = Vector{Any}(undef, nworkers())
@sync begin
    for (idx, pid) in enumerate(workers())
        @async responses[idx] = remotecall_fetch(foo, pid, args...)
    end
end
```

比...更快：

```julia
using Distributed

refs = Vector{Any}(undef, nworkers())
for (idx, pid) in enumerate(workers())
    refs[idx] = @spawnat pid foo(args...)
end
responses = [fetch(r) for r in refs]
```

前者导致每个工作者只需进行一次网络往返，而后者则导致两次网络调用 - 首先是由 [`@spawnat`](@ref) 发起，其次是由于 [`fetch`](@ref)（甚至是 [`wait`](@ref)）。`4d61726b646f776e2e436f64652822222c202266657463682229_40726566`/`4d61726b646f776e2e436f64652822222c2022776169742229_40726566` 也在串行执行，导致整体性能较差。

## Fix deprecation warnings

一个已弃用的函数内部执行查找，以便仅打印一次相关警告。这个额外的查找可能会导致显著的性能下降，因此所有已弃用函数的使用都应按照警告的建议进行修改。

## Tweaks

这些是一些可能在紧密的内部循环中有所帮助的小点。

  * 避免不必要的数组。例如，使用 `x+y+z` 而不是 [`sum([x,y,z])`](@ref)。
  * 使用 [`abs2(z)`](@ref) 替代 [`abs(z)^2`](@ref) 用于复杂的 `z`。一般来说，尝试重写代码以使用 [`abs2`](@ref) 替代 [`abs`](@ref) 用于复杂参数。
  * 使用 [`div(x,y)`](@ref) 进行整数的截断除法，而不是 [`trunc(x/y)`](@ref)，使用 [`fld(x,y)`](@ref) 而不是 [`floor(x/y)`](@ref)，以及使用 [`cld(x,y)`](@ref) 而不是 [`ceil(x/y)`](@ref)。

## [Performance Annotations](@id man-performance-annotations)

有时，通过承诺某些程序属性，可以启用更好的优化。

  * 使用 [`@inbounds`](@ref) 来消除表达式中的数组边界检查。在执行此操作之前，请确保这一点。如果下标超出范围，您可能会遭遇崩溃或静默损坏。
  * 使用 [`@fastmath`](@ref) 允许对实数进行正确的浮点优化，但可能导致 IEEE 数字的差异。在执行此操作时要小心，因为这可能会改变数值结果。这对应于 clang 的 `-ffast-math` 选项。
  * 在 `for` 循环前写上 [`@simd`](@ref) 以保证迭代是独立的并且可以重新排序。请注意，在许多情况下，Julia 可以在没有 `@simd` 宏的情况下自动向量化代码；只有在这种转换在其他情况下是非法的情况下才有益，包括允许浮点重关联和忽略依赖内存访问的情况（`@simd ivdep`）。再次强调，在断言 `@simd` 时要非常小心，因为错误地注释一个具有依赖迭代的循环可能会导致意外结果。特别要注意的是，对某些 `AbstractArray` 子类型的 `setindex!` 本质上依赖于迭代顺序。**此功能是实验性的**，在未来的 Julia 版本中可能会改变或消失。

使用 1:n 来索引 AbstractArray 的常见习语在数组使用非常规索引时并不安全，如果关闭了边界检查，可能会导致段错误。请改用 `LinearIndices(x)` 或 `eachindex(x)`（另见 [Arrays with custom indices](@ref man-custom-indices)）。

!!! note
    虽然 `@simd` 需要直接放在最内层的 `for` 循环前面，但 `@inbounds` 和 `@fastmath` 可以应用于单个表达式或出现在嵌套代码块中的所有表达式，例如，使用 `@inbounds begin` 或 `@inbounds for ...`。


这里是一个同时使用 `@inbounds` 和 `@simd` 标记的示例（我们在这里使用 `@noinline` 来防止优化器过于聪明，从而破坏我们的基准测试）：

```julia
@noinline function inner(x, y)
    s = zero(eltype(x))
    for i=eachindex(x)
        @inbounds s += x[i]*y[i]
    end
    return s
end

@noinline function innersimd(x, y)
    s = zero(eltype(x))
    @simd for i = eachindex(x)
        @inbounds s += x[i] * y[i]
    end
    return s
end

function timeit(n, reps)
    x = rand(Float32, n)
    y = rand(Float32, n)
    s = zero(Float64)
    time = @elapsed for j in 1:reps
        s += inner(x, y)
    end
    println("GFlop/sec        = ", 2n*reps / time*1E-9)
    time = @elapsed for j in 1:reps
        s += innersimd(x, y)
    end
    println("GFlop/sec (SIMD) = ", 2n*reps / time*1E-9)
end

timeit(1000, 1000)
```

在一台配备2.4GHz Intel Core i5处理器的计算机上，这会产生：

```
GFlop/sec        = 1.9467069505224963
GFlop/sec (SIMD) = 17.578554163920018
```

(`GFlop/sec` 测量性能，数字越大越好。)

这是一个包含三种标记的示例。该程序首先计算一维数组的有限差分，然后评估结果的L2范数：

```julia
function init!(u::Vector)
    n = length(u)
    dx = 1.0 / (n-1)
    @fastmath @inbounds @simd for i in 1:n #by asserting that `u` is a `Vector` we can assume it has 1-based indexing
        u[i] = sin(2pi*dx*i)
    end
end

function deriv!(u::Vector, du)
    n = length(u)
    dx = 1.0 / (n-1)
    @fastmath @inbounds du[1] = (u[2] - u[1]) / dx
    @fastmath @inbounds @simd for i in 2:n-1
        du[i] = (u[i+1] - u[i-1]) / (2*dx)
    end
    @fastmath @inbounds du[n] = (u[n] - u[n-1]) / dx
end

function mynorm(u::Vector)
    n = length(u)
    T = eltype(u)
    s = zero(T)
    @fastmath @inbounds @simd for i in 1:n
        s += u[i]^2
    end
    @fastmath @inbounds return sqrt(s)
end

function main()
    n = 2000
    u = Vector{Float64}(undef, n)
    init!(u)
    du = similar(u)

    deriv!(u, du)
    nu = mynorm(du)

    @time for i in 1:10^6
        deriv!(u, du)
        nu = mynorm(du)
    end

    println(nu)
end

main()
```

在一台配备2.7 GHz Intel Core i7处理器的计算机上，这会产生：

```
$ julia wave.jl;
  1.207814709 seconds
4.443986180758249

$ julia --math-mode=ieee wave.jl;
  4.487083643 seconds
4.443986180758249
```

在这里，选项 `--math-mode=ieee` 禁用 `@fastmath` 宏，以便我们可以比较结果。

在这种情况下，由于 `@fastmath` 的加速因素约为 3.7。这是异常大的 – 通常情况下，加速会更小。（在这个特定的例子中，基准测试的工作集足够小，可以适应处理器的 L1 缓存，因此内存访问延迟不发挥作用，计算时间主要由 CPU 使用决定。在许多现实世界的程序中情况并非如此。）此外，在这种情况下，这种优化并不会改变结果 – 通常情况下，结果会略有不同。在某些情况下，特别是对于数值不稳定的算法，结果可能会有很大不同。

注释 `@fastmath` 重新排列浮点表达式，例如改变评估顺序，或假设某些特殊情况（无穷大、非数）不会发生。在这种情况下（以及在这台特定的计算机上），主要的区别是函数 `deriv` 中的表达式 `1 / (2*dx)` 被提升出了循环（即在循环外计算），就像写成 `idx = 1 / (2*dx)` 一样。在循环中，表达式 `... / (2*dx)` 然后变成 `... * idx`，这计算起来要快得多。当然，编译器实际应用的优化以及由此产生的加速效果在很大程度上依赖于硬件。您可以通过使用 Julia 的 [`code_native`](@ref) 函数来检查生成代码的变化。

请注意，`@fastmath` 还假设在计算过程中不会出现 `NaN`，这可能会导致意外的行为：

```julia-repl
julia> f(x) = isnan(x);

julia> f(NaN)
true

julia> f_fast(x) = @fastmath isnan(x);

julia> f_fast(NaN)
false
```

## Treat Subnormal Numbers as Zeros

次正常数，之前称为 [denormal numbers](https://en.wikipedia.org/wiki/Denormal_number)，在许多上下文中非常有用，但在某些硬件上会产生性能损失。调用 [`set_zero_subnormals(true)`](@ref) 允许浮点操作将次正常输入或输出视为零，这可能会提高某些硬件的性能。调用 [`set_zero_subnormals(false)`](@ref) 强制对次正常数执行严格的 IEEE 行为。

以下是一个示例，其中次正规数明显影响某些硬件的性能：

```julia
function timestep(b::Vector{T}, a::Vector{T}, Δt::T) where T
    @assert length(a)==length(b)
    n = length(b)
    b[1] = 1                            # Boundary condition
    for i=2:n-1
        b[i] = a[i] + (a[i-1] - T(2)*a[i] + a[i+1]) * Δt
    end
    b[n] = 0                            # Boundary condition
end

function heatflow(a::Vector{T}, nstep::Integer) where T
    b = similar(a)
    for t=1:div(nstep,2)                # Assume nstep is even
        timestep(b,a,T(0.1))
        timestep(a,b,T(0.1))
    end
end

heatflow(zeros(Float32,10),2)           # Force compilation
for trial=1:6
    a = zeros(Float32,1000)
    set_zero_subnormals(iseven(trial))  # Odd trials use strict IEEE arithmetic
    @time heatflow(a,1000)
end
```

这会产生类似于的输出

```
  0.002202 seconds (1 allocation: 4.063 KiB)
  0.001502 seconds (1 allocation: 4.063 KiB)
  0.002139 seconds (1 allocation: 4.063 KiB)
  0.001454 seconds (1 allocation: 4.063 KiB)
  0.002115 seconds (1 allocation: 4.063 KiB)
  0.001455 seconds (1 allocation: 4.063 KiB)
```

注意每次偶数迭代的速度明显更快。

这个例子生成了许多次正规数，因为 `a` 中的值形成了一个指数递减的曲线，随着时间的推移逐渐变平。

将次正常数视为零时应谨慎使用，因为这样做会破坏一些恒等式，例如 `x-y == 0` 意味着 `x == y`：

```jldoctest
julia> x = 3f-38; y = 2f-38;

julia> set_zero_subnormals(true); (x - y, x == y)
(0.0f0, false)

julia> set_zero_subnormals(false); (x - y, x == y)
(1.0000001f-38, false)
```

在某些应用中，零化次正常数的替代方法是注入一点微小的噪声。例如，初始化 `a` 时，不用零，而是用：

```julia
a = rand(Float32,1000) * 1.f-9
```

## [[`@code_warntype`](@ref)](@id man-code-warntype)

宏 [`@code_warntype`](@ref)（或其函数变体 [`code_warntype`](@ref)）有时可以帮助诊断与类型相关的问题。以下是一个示例：

```julia-repl
julia> @noinline pos(x) = x < 0 ? 0 : x;

julia> function f(x)
           y = pos(x)
           return sin(y*x + 1)
       end;

julia> @code_warntype f(3.2)
MethodInstance for f(::Float64)
  from f(x) @ Main REPL[9]:1
Arguments
  #self#::Core.Const(f)
  x::Float64
Locals
  y::Union{Float64, Int64}
Body::Float64
1 ─      (y = Main.pos(x))
│   %2 = (y * x)::Float64
│   %3 = (%2 + 1)::Float64
│   %4 = Main.sin(%3)::Float64
└──      return %4
```

解释 [`@code_warntype`](@ref) 的输出，就像它的兄弟们 [`@code_lowered`](@ref)、[`@code_typed`](@ref)、[`@code_llvm`](@ref) 和 [`@code_native`](@ref) 的输出，需要一些练习。您的代码以一种在生成编译机器代码的过程中经过大量消化的形式呈现。大多数表达式都有一个类型注释，表示为 `::T`（例如，[`Float64`](@ref)）。`4d61726b646f776e2e436f64652822222c202240636f64655f7761726e747970652229_40726566` 的最重要特征是非具体类型以红色显示；由于本文件是用 Markdown 编写的，而 Markdown 没有颜色，因此在本文件中，红色文本用大写字母表示。

在顶部，函数的推断返回类型显示为 `Body::Float64`。接下来的几行表示 `f` 在 Julia 的 SSA IR 形式中的主体。编号的框是标签，表示代码中跳转的目标（通过 `goto`）。查看主体，可以看到首先发生的是调用 `pos`，返回值被推断为 `Union` 类型 `Union{Float64, Int64}`，以大写形式显示，因为它是一个非具体类型。这意味着我们无法根据输入类型知道 `pos` 的确切返回类型。然而，`y*x` 的结果是 `Float64`，无论 `y` 是 `Float64` 还是 `Int64`。最终结果是 `f(x::Float64)` 的输出不会类型不稳定，即使某些中间计算是类型不稳定的。

如何使用这些信息取决于你。显然，最好将 `pos` 固定为类型稳定：如果这样做，`f` 中的所有变量都将是具体的，其性能将是最佳的。然而，在某些情况下，这种 *短暂* 的类型不稳定可能并不太重要：例如，如果 `pos` 从未单独使用，`f` 的输出是类型稳定的（对于 [`Float64`](@ref) 输入），将保护后续代码免受类型不稳定的传播影响。这在修复类型不稳定困难或不可能的情况下尤其相关。在这种情况下，上述建议（例如，添加类型注释和/或拆分函数）是你控制类型不稳定“损害”的最佳工具。此外，请注意，即使是 Julia Base 也有类型不稳定的函数。例如，函数 [`findfirst`](@ref) 返回一个数组中找到键的索引，如果未找到则返回 `nothing`，这显然是类型不稳定。为了更容易找到可能重要的类型不稳定，包含 `missing` 或 `nothing` 的 `Union` 在颜色上用黄色高亮，而不是红色。

以下示例可能会帮助您解释标记为包含非叶类型的表达式：

  * 函数体以 `Body::Union{T1,T2})` 开始

      * 解释：具有不稳定返回类型的函数
      * 建议：使返回值类型稳定，即使你必须对其进行注解
  * `invoke Main.g(%%x::Int64)::Union{Float64, Int64}`

      * 解释：调用一个类型不稳定的函数 `g`。
      * 建议：修复该函数，或在必要时注释返回值
  * `invoke Base.getindex(%%x::Array{Any,1}, 1::Int64)::Any`

      * 解释：访问类型不明确的数组元素
      * 建议：使用更明确定义类型的数组，或者在必要时注释单个元素访问的类型。
  * `Base.getfield(%%x, :(:data))::Array{Float64,N} where N`

      * 解释：获取一个非叶子类型的字段。在这种情况下，`x` 的类型，比如 `ArrayContainer`，有一个字段 `data::Array{T}`。但是 `Array` 还需要维度 `N`，才能成为一个具体类型。
      * 建议：使用具体类型，例如 `Array{T,3}` 或 `Array{T,N}`，其中 `N` 现在是 `ArrayContainer` 的一个参数。

## [Performance of captured variable](@id man-performance-captured)

考虑以下定义内部函数的示例：

```julia
function abmult(r::Int)
    if r < 0
        r = -r
    end
    f = x -> x * r
    return f
end
```

函数 `abmult` 返回一个函数 `f`，该函数将其参数乘以 `r` 的绝对值。分配给 `f` 的内部函数称为“闭包”。内部函数也被语言用于 `do` 块和生成器表达式。

这种代码风格给语言带来了性能挑战。解析器在将其转换为低级指令时，显著地重组了上述代码，通过将内部函数提取到一个单独的代码块中。像 `r` 这样的“捕获”变量，它们被内部函数和其封闭作用域共享，也被提取到一个堆分配的“盒子”中，以便内部和外部函数都可以访问，因为语言规定内部作用域中的 `r` 必须与外部作用域中的 `r` 相同，即使外部作用域（或另一个内部函数）修改了 `r`。

前一段讨论提到了“解析器”，即在包含 `abmult` 的模块首次加载时发生的编译阶段，而不是首次调用时的后续阶段。解析器并不知道 `Int` 是一个固定类型，或者语句 `r = -r` 将一个 `Int` 转换为另一个 `Int`。类型推断的魔力发生在编译的后续阶段。

因此，解析器并不知道 `r` 具有固定类型（`Int`），也不知道 `r` 在内部函数创建后不会改变值（因此不需要盒子）。因此，解析器生成的代码为盒子，盒子中包含一个具有抽象类型的对象，例如 `Any`，这需要在每次出现 `r` 时进行运行时类型调度。这可以通过对上述函数应用 `@code_warntype` 来验证。盒装和运行时类型调度都可能导致性能损失。

如果在代码的性能关键部分使用了捕获的变量，那么以下提示有助于确保它们的使用是高效的。首先，如果已知捕获的变量不会改变其类型，则可以通过类型注释（在变量上，而不是右侧）显式声明这一点：

```julia
function abmult2(r0::Int)
    r::Int = r0
    if r < 0
        r = -r
    end
    f = x -> x * r
    return f
end
```

类型注解部分恢复了由于捕获而丢失的性能，因为解析器可以将具体类型与盒子中的对象关联起来。进一步说，如果捕获的变量根本不需要被装箱（因为在闭包创建后不会被重新赋值），可以通过以下 `let` 块来指示这一点。

```julia
function abmult3(r::Int)
    if r < 0
        r = -r
    end
    f = let r = r
            x -> x * r
    end
    return f
end
```

`let` 块创建了一个新变量 `r`，其作用域仅限于内部函数。第二种技术在捕获变量的情况下恢复了完整的语言性能。请注意，这是编译器的一个快速发展的方面，未来的版本可能不需要这种程度的程序员注释来达到性能。与此同时，一些用户贡献的包，如 [FastClosures](https://github.com/c42f/FastClosures.jl)，自动插入 `let` 语句，如 `abmult3` 中所示。

## [Multithreading and linear algebra](@id man-multithreading-linear-algebra)

本节适用于多线程的 Julia 代码，在每个线程中执行线性代数操作。实际上，这些线性代数操作涉及 BLAS / LAPACK 调用，而这些调用本身也是多线程的。在这种情况下，必须确保由于这两种不同类型的多线程，核心不会被过度订阅。

Julia 编译并使用其自己的 OpenBLAS 副本进行线性代数，其线程数由环境变量 `OPENBLAS_NUM_THREADS` 控制。它可以在启动 Julia 时作为命令行选项设置，或者在 Julia 会话中通过 `BLAS.set_num_threads(N)` 修改（子模块 `BLAS` 由 `using LinearAlgebra` 导出）。可以通过 `BLAS.get_num_threads()` 访问其当前值。

当用户没有指定任何内容时，Julia 会尝试为 OpenBLAS 线程数选择一个合理的值（例如，基于平台、Julia 版本等）。然而，通常建议手动检查并设置该值。OpenBLAS 的行为如下：

  * 如果 `OPENBLAS_NUM_THREADS=1`，OpenBLAS 使用调用的 Julia 线程，即它“存在于”运行计算的 Julia 线程中。
  * 如果 `OPENBLAS_NUM_THREADS=N>1`，OpenBLAS 会创建并管理自己的线程池（总共 `N` 个）。所有 Julia 线程共享一个 OpenBLAS 线程池。

当您使用 `JULIA_NUM_THREADS=X` 启动 Julia 的多线程模式时，通常建议将 `OPENBLAS_NUM_THREADS` 设置为 1。根据上述行为，将 BLAS 线程数增加到 `N>1` 很容易导致性能下降，特别是当 `N<<X` 时。然而，这只是一个经验法则，设置每个线程数的最佳方法是根据您的具体应用进行实验。

## [Alternative linear algebra backends](@id man-backends-linear-algebra)

作为 OpenBLAS 的替代方案，存在几个其他后端可以帮助提高线性代数性能。显著的例子包括 [MKL.jl](https://github.com/JuliaLinearAlgebra/MKL.jl) 和 [AppleAccelerate.jl](https://github.com/JuliaMath/AppleAccelerate.jl)。

这些是外部包，因此我们在这里不会详细讨论它们。请参考它们各自的文档（特别是因为它们在多线程方面的行为与 OpenBLAS 不同）。

## Execution latency, package loading and package precompiling time

### Reducing time to first plot etc.

第一次调用 Julia 方法时，它（以及它调用的任何方法，或可以静态确定的方法）将被编译。[`@time`](@ref) 宏系列说明了这一点。

```
julia> foo() = rand(2,2) * rand(2,2)
foo (generic function with 1 method)

julia> @time @eval foo();
  0.252395 seconds (1.12 M allocations: 56.178 MiB, 2.93% gc time, 98.12% compilation time)

julia> @time @eval foo();
  0.000156 seconds (63 allocations: 2.453 KiB)
```

请注意，`@time @eval` 更适合测量编译时间，因为如果没有 [`@eval`](@ref)，某些编译可能在计时开始之前已经完成。

在开发一个包时，您可以通过 *预编译* 来改善用户体验，以便在他们使用该包时，所用的代码已经被编译。为了有效地预编译包代码，建议使用 [`PrecompileTools.jl`](https://julialang.github.io/PrecompileTools.jl/stable/) 在预编译期间运行一个“预编译工作负载”，该工作负载代表典型的包使用情况，这将把本地编译的代码缓存到包的 `pkgimage` 缓存中，从而大大减少此类使用的“首次执行时间”（通常称为 TTFX）。

请注意，[`PrecompileTools.jl`](https://julialang.github.io/PrecompileTools.jl/stable/) 工作负载可以被禁用，有时可以通过首选项进行配置，如果您不想花额外的时间进行预编译，这在开发包时可能是一个情况。

### Reducing package loading time

保持加载包所需的时间通常是有帮助的。包开发者的一般良好实践包括：

1. 减少您的依赖项，仅保留真正需要的。考虑使用 [package extensions](@ref) 来支持与其他包的互操作性，而不增加您基本依赖项的负担。
2. 避免使用 [`__init__()`](@ref) 函数，除非没有其他选择，特别是那些可能触发大量编译或执行时间较长的函数。
3. 在可能的情况下，修复 [invalidations](https://julialang.org/blog/2020/08/invalidations/) 以及你的依赖项和包代码中的相关内容。

工具 [`@time_imports`](@ref) 在 REPL 中可以用来审查上述因素。

```julia-repl
julia> @time @time_imports using Plots
      0.5 ms  Printf
     16.4 ms  Dates
      0.7 ms  Statistics
               ┌ 23.8 ms SuiteSparse_jll.__init__() 86.11% compilation time (100% recompilation)
     90.1 ms  SuiteSparse_jll 91.57% compilation time (82% recompilation)
      0.9 ms  Serialization
               ┌ 39.8 ms SparseArrays.CHOLMOD.__init__() 99.47% compilation time (100% recompilation)
    166.9 ms  SparseArrays 23.74% compilation time (100% recompilation)
      0.4 ms  Statistics → SparseArraysExt
      0.5 ms  TOML
      8.0 ms  Preferences
      0.3 ms  PrecompileTools
      0.2 ms  Reexport
... many deps omitted for example ...
      1.4 ms  Tar
               ┌ 73.8 ms p7zip_jll.__init__() 99.93% compilation time (100% recompilation)
     79.4 ms  p7zip_jll 92.91% compilation time (100% recompilation)
               ┌ 27.7 ms GR.GRPreferences.__init__() 99.77% compilation time (100% recompilation)
     43.0 ms  GR 64.26% compilation time (100% recompilation)
               ┌ 2.1 ms Plots.__init__() 91.80% compilation time (100% recompilation)
    300.9 ms  Plots 0.65% compilation time (100% recompilation)
  1.795602 seconds (3.33 M allocations: 190.153 MiB, 7.91% gc time, 39.45% compilation time: 97% of which was recompilation)

```

注意，在这个例子中加载了多个包，其中一些具有 `__init__()` 函数，有些会导致编译，而有些则是重新编译。重新编译是由于早期的包使方法失效，然后在这些情况下，当后续的包运行它们的 `__init__()` 函数时，有些会在代码可以运行之前触发重新编译。

此外，请注意 `Statistics` 扩展 `SparseArraysExt` 已被激活，因为 `SparseArrays` 在依赖树中。即，见 `0.4 ms  Statistics → SparseArraysExt`。

本报告提供了一个很好的机会来审查依赖加载时间的成本是否值得其带来的功能。此外，`Pkg` 工具的 `why` 可以用来报告为什么存在间接依赖。

```
(CustomPackage) pkg> why FFMPEG_jll
  Plots → FFMPEG → FFMPEG_jll
  Plots → GR → GR_jll → FFMPEG_jll
```

或者要查看一个包带来的间接依赖，你可以使用 `pkg> rm` 删除该包，查看从清单中移除的依赖，然后使用 `pkg> undo` 撤销更改。

如果加载时间主要受到慢速 `__init__()` 方法的影响，识别正在编译的内容的一种详细方法是使用 Julia 参数 `--trace-compile=stderr`，这将在每次编译方法时报告一个 [`precompile`](@ref) 语句。例如，完整的设置将是：

```
$ julia --startup-file=no --trace-compile=stderr
julia> @time @time_imports using CustomPackage
...
```

注意 `--startup-file=no`，这有助于将测试与您在 `startup.jl` 中可能拥有的包隔离开。

对重新编译原因的更多分析可以通过 [`SnoopCompile`](https://github.com/timholy/SnoopCompile.jl) 包来实现。
