# Style Guide

以下部分解释了几种习惯性Julia编码风格的方面。 这些规则都不是绝对的；它们只是建议，旨在帮助您熟悉该语言，并帮助您在替代设计中进行选择。

## Indentation

使用每个缩进级别4个空格。

## Write functions, not just scripts

将代码作为一系列顶层步骤编写是快速开始解决问题的一种方法，但您应该尽快尝试将程序划分为函数。函数更具可重用性和可测试性，并且可以明确正在执行的步骤及其输入和输出。此外，由于Julia编译器的工作方式，函数内部的代码往往比顶层代码运行得更快。

值得强调的是，函数应该接受参数，而不是直接操作全局变量（除了像 [`pi`](@ref) 这样的常量）。

## Avoid writing overly-specific types

代码应该尽可能通用。不要写：

```julia
Complex{Float64}(x)
```

最好使用可用的通用函数：

```julia
complex(float(x))
```

第二个版本将把 `x` 转换为适当的类型，而不是始终转换为相同的类型。

这个风格要点特别与函数参数相关。例如，如果一个参数实际上可以是任何整数，使用抽象类型 [`Integer`](@ref)，就不要声明参数为类型 `Int` 或 [`Int32`](@ref)。事实上，在许多情况下，您可以完全省略参数类型，除非需要与其他方法定义进行区分，因为如果传递了不支持任何必要操作的类型，反正会抛出 [`MethodError`](@ref)。 （这被称为 [duck typing](https://en.wikipedia.org/wiki/Duck_typing)。）

例如，考虑以下函数 `addone` 的定义，该函数返回其参数加一：

```julia
addone(x::Int) = x + 1                 # works only for Int
addone(x::Integer) = x + oneunit(x)    # any integer type
addone(x::Number) = x + oneunit(x)     # any numeric type
addone(x) = x + oneunit(x)             # any type supporting + and oneunit
```

最后一个 `addone` 的定义处理任何支持 [`oneunit`](@ref) 的类型（它以与 `x` 相同的类型返回 1，从而避免了不必要的类型提升）以及带有这些参数的 [`+`](@ref) 函数。关键是要意识到，定义 *仅* 一般的 `addone(x) = x + oneunit(x)` 并没有 *任何性能损失*，因为 Julia 会根据需要自动编译专门版本。例如，当你第一次调用 `addone(12)` 时，Julia 会自动为 `x::Int` 参数编译一个专门的 `addone` 函数，并将对 `oneunit` 的调用替换为它的内联值 `1`。因此，上面前三个 `addone` 的定义与第四个定义完全冗余。

## Handle excess argument diversity in the caller

而不是：

```julia
function foo(x, y)
    x = Int(x); y = Int(y)
    ...
end
foo(x, y)
```

使用：

```julia
function foo(x::Int, y::Int)
    ...
end
foo(Int(x), Int(y))
```

这是一种更好的风格，因为 `foo` 并不真正接受所有类型的数字；它实际上需要 `Int`。

一个问题是，如果一个函数本质上需要整数，那么强制调用者决定如何转换非整数（例如，向下取整或向上取整）可能更好。另一个问题是，声明更具体的类型为未来的方法定义留出了更多的“空间”。

## [Append `!` to names of functions that modify their arguments](@id bang-convention)

而不是：

```julia
function double(a::AbstractArray{<:Number})
    for i in eachindex(a)
        a[i] *= 2
    end
    return a
end
```

使用：

```julia
function double!(a::AbstractArray{<:Number})
    for i in eachindex(a)
        a[i] *= 2
    end
    return a
end
```

Julia Base 在整个过程中使用了这种约定，并包含了同时具有复制和修改形式的函数示例（例如，[`sort`](@ref) 和 [`sort!`](@ref)），以及其他仅仅是修改的函数（例如，[`push!`](@ref)，[`pop!`](@ref)，[`splice!`](@ref)）。 这种函数通常也会返回修改后的数组以方便使用。

与 IO 或使用随机数生成器 (RNG) 相关的函数是显著的例外：由于这些函数几乎总是必须改变 IO 或 RNG，因此以 `!` 结尾的函数用于表示一种 *不同于* 改变 IO 或推进 RNG 状态的变更。例如，`rand(x)` 改变了 RNG，而 `rand!(x)` 则同时改变了 RNG 和 `x`；类似地，`read(io)` 改变了 `io`，而 `read!(io, x)` 则同时改变了两个参数。

## Avoid strange type `Union`s

类型如 `Union{Function,AbstractString}` 通常是某些设计可以更清晰的标志。

## Avoid elaborate container types

通常构建如下数组并没有太大帮助：

```julia
a = Vector{Union{Int,AbstractString,Tuple,Array}}(undef, n)
```

在这种情况下 `Vector{Any}(undef, n)` 更好。为特定用途添加注释（例如 `a[i]::Int`）对编译器也更有帮助，而不是试图将多种替代方案打包成一种类型。

## Prefer exported methods over direct field access

习惯用法的 Julia 代码通常应将模块导出的函数视为其类型的接口。对象的字段通常被视为实现细节，用户代码只有在明确说明这是 API 的情况下才能直接访问它们。这有几个好处：

  * 包开发者可以更自由地更改实现，而不会破坏用户代码。
  * 方法可以传递给高阶构造，例如 [`map`](@ref)（例如 `map(imag, zs)`），而不是 `[z.im for z in zs]`）。
  * 方法可以在抽象类型上定义。
  * 方法可以描述一个可以在不同类型之间共享的概念操作（例如，`real(z)` 可以作用于复数或四元数）。

Julia的调度系统鼓励这种风格，因为`play(x::MyType)`仅在该特定类型上定义了`play`方法，其他类型可以有自己的实现。

类似地，未导出的函数通常是内部的，并且可能会发生变化，除非文档另有说明。名称有时会加上 `_` 前缀（或后缀）以进一步表明某些内容是“内部的”或实现细节，但这并不是一条规则。

反例包括 [`NamedTuple`](@ref)，[`RegexMatch`](@ref match)，[`StatStruct`](@ref stat)。

## Use naming conventions consistent with Julia `base/`

  * 模块和类型名称使用大写和驼峰命名法：`module SparseArrays`，`struct UnitRange`。
  * 函数是小写的（[`maximum`](@ref)，[`convert`](@ref)），并且在可读时，多个单词紧凑在一起（[`isequal`](@ref)，[`haskey`](@ref)）。必要时，使用下划线作为单词分隔符。下划线也用于表示概念的组合（[`remotecall_fetch`](@ref) 作为 `fetch(remotecall(...))` 的更高效实现）或作为修饰符。
  * 函数如果改变了至少一个参数，名称以 `!` 结尾。
  * 简洁性被重视，但避免缩写（[`indexin`](@ref) 而不是 `indxin`），因为这会使人难以记住特定单词是否以及如何被缩写。

如果一个函数名称需要多个单词，请考虑它是否可能代表多个概念，并且可能更好地拆分成几个部分。

## Write functions with argument ordering similar to Julia Base

作为一般规则，Base 库在适用的情况下使用以下参数顺序来调用函数：

1. **函数参数**。将函数参数放在首位允许使用 [`do`](@ref) 块来传递多行匿名函数。
2. **I/O 流**。首先指定 `IO` 对象允许将函数传递给诸如 [`sprint`](@ref) 的函数，例如 `sprint(show, x)`。
3. **输入正在被改变**。例如，在 [`fill!(x, v)`](@ref fill!) 中，`x` 是正在被改变的对象，它出现在要插入到 `x` 中的值之前。
4. **类型**。传递一个类型通常意味着输出将具有给定的类型。在 [`parse(Int, "1")`](@ref parse) 中，类型出现在要解析的字符串之前。有许多这样的例子，其中类型首先出现，但值得注意的是，在 [`read(io, String)`](@ref read) 中，`IO` 参数出现在类型之前，这与这里概述的顺序一致。
5. **输入未被改变**。在 `fill!(x, v)` 中，`v` *没有* 被改变，并且它在 `x` 之后。
6. **键**。对于关联集合，这是键值对的键。对于其他索引集合，这是索引。
7. **值**。对于关联集合，这是键值对的值。在像 [`fill!(x, v)`](@ref fill!) 这样的情况下，这个值是 `v`。
8. **其他一切**。任何其他论点。
9. **可变参数**。这指的是在函数调用的末尾可以无限列出的参数。例如，在 `Matrix{T}(undef, dims)` 中，维度可以作为 [`Tuple`](@ref) 给出，例如 `Matrix{T}(undef, (1,2))`，或者作为 [`Vararg`](@ref) 给出，例如 `Matrix{T}(undef, 1, 2)`。
10. **关键字参数**。在Julia中，关键字参数在函数定义中必须放在最后；这里列出它们是为了完整性。

绝大多数函数不会接受上述列出的每种参数；这些数字仅表示应对函数的任何适用参数使用的优先级。

当然有一些例外。例如，在 [`convert`](@ref) 中，类型应该始终放在第一位。在 [`setindex!`](@ref) 中，值在索引之前，以便可以将索引作为可变参数提供。

在设计API时，尽可能遵循这个一般顺序可能会为您的函数用户提供更一致的体验。

## Don't overuse try-catch

避免错误总比依赖于捕捉错误要好。

## Don't parenthesize conditions

Julia 不需要在 `if` 和 `while` 的条件周围加括号。写：

```julia
if a == b
```

而不是：

```julia
if (a == b)
```

## Don't overuse `...`

拼接函数参数可能会上瘾。与其使用 `[a..., b...]`，不如简单地使用 `[a; b]`，这已经可以连接数组。[`collect(a)`](@ref) 比 `[a...]` 更好，但由于 `a` 已经是可迭代的，通常更好的做法是保持原样，而不是将其转换为数组。

## Ensure constructors return an instance of their own type

当在类型 `T` 上调用方法 `T(x)` 时，通常期望返回类型为 T 的值。定义一个 [constructor](@ref man-constructors) 返回一个意外类型可能会导致混淆和不可预测的行为：

```jldoctest
julia> struct Foo{T}
           x::T
       end

julia> Base.Float64(foo::Foo) = Foo(Float64(foo.x))  # Do not define methods like this

julia> Float64(Foo(3))  # Should return `Float64`
Foo{Float64}(3.0)

julia> Foo{Int}(x) = Foo{Float64}(x)  # Do not define methods like this

julia> Foo{Int}(3)  # Should return `Foo{Int}`
Foo{Float64}(3.0)
```

为了保持代码的清晰性并确保类型一致性，始终设计构造函数以返回它们应该构造的类型的实例。

## Don't use unnecessary static parameters

一个函数签名：

```julia
foo(x::T) where {T<:Real} = ...
```

应该写成：

```julia
foo(x::Real) = ...
```

相反，特别是如果 `T` 在函数体中未被使用。即使 `T` 被使用，如果方便的话，可以用 [`typeof(x)`](@ref) 替换。没有性能差异。请注意，这并不是对静态参数的一般警告，而只是针对不必要的使用。

请注意，容器类型，特别是在函数调用中可能需要类型参数。有关更多信息，请参见常见问题解答 [Avoid fields with abstract containers](@ref)。

## Avoid confusion about whether something is an instance or a type

像以下这样的定义集合令人困惑：

```julia
foo(::Type{MyType}) = ...
foo(::MyType) = foo(MyType)
```

决定该概念是写作 `MyType` 还是 `MyType()`，并坚持使用。

首选风格是默认使用实例，只有在解决某些问题时才添加涉及 `Type{MyType}` 的方法。

如果一个类型实际上是一个枚举，它应该被定义为一个单一的（理想情况下是不可变的结构体或原始）类型，枚举值是它的实例。构造函数和转换可以检查值是否有效。这种设计优于将枚举定义为一个抽象类型，"值"作为子类型。

## Don't overuse macros

注意何时宏实际上可以是一个函数。

在宏中调用 [`eval`](@ref) 是一个特别危险的警告信号；这意味着该宏仅在顶层调用时才能工作。如果这样的宏被写成一个函数，它自然会访问所需的运行时值。

## Don't expose unsafe operations at the interface level

如果你有一个使用原生指针的类型：

```julia
mutable struct NativeType
    p::Ptr{UInt8}
    ...
end
```

请不要写如下定义：

```julia
getindex(x::NativeType, i) = unsafe_load(x.p, i)
```

问题在于这种类型的用户可以在没有意识到操作不安全的情况下写 `x[i]`，从而容易受到内存错误的影响。

这样的函数应该要么检查操作以确保其安全，要么在其名称中包含 `unsafe` 以提醒调用者。

## Don't overload methods of base container types

可以写出如下定义：

```julia
show(io::IO, v::Vector{MyType}) = ...
```

这将提供具有特定新元素类型的向量的自定义显示。虽然很诱人，但应该避免这样做。问题在于，用户会期望一个众所周知的类型，如 `Vector()`，以某种方式运行，过度自定义其行为可能会使其更难以使用。

## [Avoid type piracy](@id avoid-type-piracy)

“类型盗用”是指在您未定义的类型上扩展或重新定义 Base 或其他包中的方法的做法。在极端情况下，您可能会导致 Julia 崩溃（例如，如果您的方法扩展或重新定义导致无效输入被传递给 `ccall`）。类型盗用可能会使代码推理变得复杂，并可能引入难以预测和诊断的不兼容性。

作为一个例子，假设你想在一个模块中定义符号的乘法：

```julia
module A
import Base.*
*(x::Symbol, y::Symbol) = Symbol(x,y)
end
```

问题是现在任何其他使用 `Base.*` 的模块也会看到这个定义。由于 `Symbol` 在 Base 中定义并被其他模块使用，这可能会意外地改变无关代码的行为。这里有几种替代方案，包括使用不同的函数名称，或者将 `Symbol` 包装在你定义的另一种类型中。

有时，配对的包可能会进行类型盗用，以将特性与定义分开，特别是当这些包是由合作作者设计时，并且定义是可重用的。例如，一个包可能提供一些用于处理颜色的有用类型；另一个包可以为这些类型定义方法，以实现颜色空间之间的转换。另一个例子可能是一个作为某些 C 代码的薄包装的包，另一个包可能会盗用它以实现更高级的、友好的 Julia API。

## Be careful with type equality

您通常想要使用 [`isa`](@ref) 和 [`<:`](@ref) 来测试类型，而不是使用 `==`。检查类型的精确相等通常只有在与已知的具体类型（例如 `T == Float64`）进行比较时才有意义，或者如果您 *真的，真的* 知道自己在做什么。

## Don't write a trivial anonymous function `x->f(x)` for a named function `f`

由于高阶函数通常与匿名函数一起调用，因此很容易得出这是可取的甚至是必要的结论。但是，任何函数都可以直接传递，而无需“包装”在匿名函数中。与其写 `map(x->f(x), a)`，不如写 [`map(f, a)`](@ref)。

## Avoid using floats for numeric literals in generic code when possible

如果您编写处理数字的通用代码，并且可以预期它将与许多不同的数字类型参数一起运行，请尝试使用对参数影响尽可能小的数字类型字面量。

例如，

```jldoctest
julia> f(x) = 2.0 * x
f (generic function with 1 method)

julia> f(1//2)
1.0

julia> f(1/2)
1.0

julia> f(1)
2.0
```

当

```jldoctest
julia> g(x) = 2 * x
g (generic function with 1 method)

julia> g(1//2)
1//1

julia> g(1/2)
1.0

julia> g(1)
2
```

如您所见，第二个版本中我们使用了 `Int` 字面量，保留了输入参数的类型，而第一个版本则没有。这是因为例如 `promote_type(Int, Float64) == Float64`，并且在乘法中发生了类型提升。同样，[`Rational`](@ref) 字面量的类型干扰性低于 [`Float64`](@ref) 字面量，但高于 `Int`：

```jldoctest
julia> h(x) = 2//1 * x
h (generic function with 1 method)

julia> h(1//2)
1//1

julia> h(1/2)
1.0

julia> h(1)
2//1
```

因此，在可能的情况下使用 `Int` 字面量，对于字面非整数数字使用 `Rational{Int}`，以便更容易使用您的代码。
