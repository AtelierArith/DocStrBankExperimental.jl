# [Constructors](@id man-constructors)

构造函数 [^1] 是创建新对象的函数 – 特别是 [Composite Types](@ref) 的实例。在 Julia 中，类型对象也充当构造函数：当将参数元组作为函数应用时，它们会创建自身的新实例。这一点在介绍复合类型时已经简要提到过。例如：

```jldoctest footype
julia> struct Foo
           bar
           baz
       end

julia> foo = Foo(1, 2)
Foo(1, 2)

julia> foo.bar
1

julia> foo.baz
2
```

对于许多类型，通过将它们的字段值绑定在一起来形成新对象通常是创建实例所需的全部。然而，在某些情况下，创建复合对象时需要更多的功能。有时必须强制执行不变性，或者通过检查参数或转换它们来实现。[Recursive data structures](https://en.wikipedia.org/wiki/Recursion_%28computer_science%29#Recursive_data_structures_.28structural_recursion.29)，尤其是那些可能是自引用的对象，通常无法在没有首先以不完整状态创建的情况下干净地构造，然后通过编程方式进行更改以使其完整，这与对象创建是一个单独的步骤。有时，能够使用比它们的字段更少或不同类型的参数来构造对象是很方便的。Julia 的对象构造系统解决了所有这些情况及更多问题。

[^1]: Nomenclature: while the term "constructor" generally refers to the entire function which constructs objects of a type, it is common to abuse terminology slightly and refer to specific constructor methods as "constructors". In such situations, it is generally clear from the context that the term is used to mean "constructor method" rather than "constructor function", especially as it is often used in the sense of singling out a particular method of the constructor from all of the others.

## [Outer Constructor Methods](@id man-outer-constructor-methods)

构造函数就像Julia中的其他函数一样，其整体行为由其方法的组合行为定义。因此，您可以通过简单地定义新方法来为构造函数添加功能。例如，假设您想为`Foo`对象添加一个只接受一个参数的构造函数方法，并将给定值用于`bar`和`baz`字段。这很简单：

```jldoctest footype
julia> Foo(x) = Foo(x,x)
Foo

julia> Foo(1)
Foo(1, 1)
```

您还可以添加一个零参数的 `Foo` 构造方法，为 `bar` 和 `baz` 字段提供默认值：

```jldoctest footype
julia> Foo() = Foo(0)
Foo

julia> Foo()
Foo(0, 0)
```

这里的零参数构造方法调用了单参数构造方法，而单参数构造方法又调用了自动提供的双参数构造方法。出于很快会变得清晰的原因，像这样声明为普通方法的额外构造方法被称为*外部*构造方法。外部构造方法只能通过调用另一个构造方法（例如自动提供的默认构造方法）来创建新实例。

## [Inner Constructor Methods](@id man-inner-constructor-methods)

虽然外部构造方法成功地解决了提供额外便利方法以构造对象的问题，但它们未能解决本章引言中提到的其他两个用例：强制不变性和允许构造自引用对象。对于这些问题，需要*内部*构造方法。内部构造方法类似于外部构造方法，但有两个不同之处：

1. 它是在类型声明的块内声明的，而不是像普通方法那样在外部声明。
2. 它可以访问一个特殊的本地存在的函数，称为 [`new`](@ref)，该函数创建块类型的对象。

例如，假设有人想声明一个类型，用于保存一对实数，前提是第一个数字不大于第二个数字。可以这样声明：

```jldoctest pairtype
julia> struct OrderedPair
           x::Real
           y::Real
           OrderedPair(x,y) = x > y ? error("out of order") : new(x,y)
       end
```

现在 `OrderedPair` 对象只能在 `x <= y` 的情况下构造：

```jldoctest pairtype; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> OrderedPair(1, 2)
OrderedPair(1, 2)

julia> OrderedPair(2,1)
ERROR: out of order
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] OrderedPair(::Int64, ::Int64) at ./none:4
 [3] top-level scope
```

如果类型被声明为 `mutable`，你可以直接更改字段值，从而违反这个不变性。当然，未经允许地干扰对象的内部结构是不好的做法。你（或其他人）也可以在任何后期提供额外的外部构造方法，但一旦类型被声明，就无法添加更多的内部构造方法。由于外部构造方法只能通过调用其他构造方法来创建对象，因此最终必须调用某个内部构造方法来创建对象。这保证了所有声明类型的对象必须通过调用与该类型提供的某个内部构造方法而存在，从而在一定程度上强制执行类型的不变性。

如果定义了任何内部构造方法，则不会提供默认构造方法：这意味着您已经为自己提供了所需的所有内部构造函数。默认构造函数等同于编写自己的内部构造方法，该方法将对象的所有字段作为参数（如果相应字段具有类型，则限制为正确的类型），并将它们传递给 `new`，返回生成的对象：

```jldoctest
julia> struct Foo
           bar
           baz
           Foo(bar,baz) = new(bar,baz)
       end

```

此声明与早期的 `Foo` 类型定义具有相同的效果，而无需显式的内部构造方法。以下两种类型是等效的 - 一种具有默认构造函数，另一种具有显式构造函数：

```jldoctest
julia> struct T1
           x::Int64
       end

julia> struct T2
           x::Int64
           T2(x) = new(x)
       end

julia> T1(1)
T1(1)

julia> T2(1)
T2(1)

julia> T1(1.0)
T1(1)

julia> T2(1.0)
T2(1)
```

提供尽可能少的内部构造方法是一种良好的实践：仅提供那些显式接受所有参数并强制执行必要错误检查和转换的方法。额外的便利构造方法，提供默认值或辅助转换，应作为外部构造方法提供，这些外部构造方法调用内部构造方法来完成繁重的工作。这种分离通常是相当自然的。

## Incomplete Initialization

尚未解决的最终问题是自引用对象的构造，或更一般地说，递归数据结构。由于根本困难可能并不立即显而易见，让我们简要解释一下。考虑以下递归类型声明：

```jldoctest selfrefer
julia> mutable struct SelfReferential
           obj::SelfReferential
       end

```

这种类型看起来可能无害，直到考虑如何构造它的实例。如果 `a` 是 `SelfReferential` 的一个实例，那么可以通过以下调用创建第二个实例：

```julia-repl
julia> b = SelfReferential(a)
```

但是，当没有实例存在以提供有效值给其 `obj` 字段时，如何构造第一个实例呢？唯一的解决方案是允许创建一个未完全初始化的 `SelfReferential` 实例，其 `obj` 字段未分配，并将该不完整实例用作另一个实例的 `obj` 字段的有效值，例如，作为它自身。

为了允许创建未完全初始化的对象，Julia 允许调用 [`new`](@ref) 函数，传入的字段数量少于类型的字段数量，从而返回一个未初始化的字段的对象。内部构造方法可以使用这个不完整的对象，在返回之前完成其初始化。这里，例如，另一个定义 `SelfReferential` 类型的尝试，这次使用一个零参数的内部构造函数返回具有指向自身的 `obj` 字段的实例：

```jldoctest selfrefer2
julia> mutable struct SelfReferential
           obj::SelfReferential
           SelfReferential() = (x = new(); x.obj = x)
       end

```

我们可以验证这个构造函数的工作原理，并构造出实际上是自引用的对象：

```jldoctest selfrefer2
julia> x = SelfReferential();

julia> x === x
true

julia> x === x.obj
true

julia> x === x.obj.obj
true
```

尽管从内部构造函数返回一个完全初始化的对象通常是个好主意，但返回未完全初始化的对象也是可能的：

```jldoctest incomplete
julia> mutable struct Incomplete
           data
           Incomplete() = new()
       end

julia> z = Incomplete();
```

虽然您可以创建具有未初始化字段的对象，但对未初始化引用的任何访问都是立即错误：

```jldoctest incomplete
julia> z.data
ERROR: UndefRefError: access to undefined reference
```

这避免了不断检查 `null` 值的需要。然而，并非所有对象字段都是引用。Julia 将某些类型视为“普通数据”，这意味着它们的所有数据都是自包含的，并且不引用其他对象。普通数据类型包括原始类型（例如 `Int`）和其他普通数据类型的不可变结构（另见：[`isbits`](@ref)，[`isbitstype`](@ref)）。普通数据类型的初始内容是未定义的：

```julia-repl
julia> struct HasPlain
           n::Int
           HasPlain() = new()
       end

julia> HasPlain()
HasPlain(438103441441)
```

普通数据类型的数组表现出相同的行为。

您可以将不完整的对象从内部构造函数传递给其他函数，以委托它们的完成：

```jldoctest
julia> mutable struct Lazy
           data
           Lazy(v) = complete_me(new(), v)
       end
```

与从构造函数返回的不完整对象一样，如果 `complete_me` 或其任何被调用者在 `Lazy` 对象初始化之前尝试访问 `data` 字段，将立即抛出错误。

## Parametric Constructors

参数化类型为构造函数的故事增添了一些复杂性。回想一下 [Parametric Types](@ref)，默认情况下，参数化复合类型的实例可以通过显式给定类型参数或通过构造函数给定的参数类型隐含的类型参数来构造。以下是一些示例：

```jldoctest parametric; filter = r"Closest candidates.*\n  .*"
julia> struct Point{T<:Real}
           x::T
           y::T
       end

julia> Point(1,2) ## implicit T ##
Point{Int64}(1, 2)

julia> Point(1.0,2.5) ## implicit T ##
Point{Float64}(1.0, 2.5)

julia> Point(1,2.5) ## implicit T ##
ERROR: MethodError: no method matching Point(::Int64, ::Float64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, ::T) where T<:Real at none:2

julia> Point{Int64}(1, 2) ## explicit T ##
Point{Int64}(1, 2)

julia> Point{Int64}(1.0,2.5) ## explicit T ##
ERROR: InexactError: Int64(2.5)
Stacktrace:
[...]

julia> Point{Float64}(1.0, 2.5) ## explicit T ##
Point{Float64}(1.0, 2.5)

julia> Point{Float64}(1,2) ## explicit T ##
Point{Float64}(1.0, 2.0)
```

如您所见，对于具有显式类型参数的构造函数调用，参数会被转换为隐含的字段类型：`Point{Int64}(1,2)` 可以正常工作，但 `Point{Int64}(1.0,2.5)` 在将 `2.5` 转换为 [`Int64`](@ref) 时会引发 [`InexactError`](@ref)。当类型由构造函数调用的参数隐含时，例如 `Point(1,2)`，则参数的类型必须一致——否则无法确定 `T`——但可以将任何一对匹配类型的实数参数传递给通用的 `Point` 构造函数。

这里真正发生的事情是 `Point`、`Point{Float64}` 和 `Point{Int64}` 都是不同的构造函数。实际上，`Point{T}` 是每种类型 `T` 的一个独特构造函数。如果没有显式提供内部构造函数，复合类型 `Point{T<:Real}` 的声明会自动为每种可能的类型 `T<:Real` 提供一个内部构造函数 `Point{T}`，其行为与非参数默认内部构造函数相同。它还提供了一个通用的外部 `Point` 构造函数，该构造函数接受一对实数参数，这些参数必须是相同类型的。这种构造函数的自动提供相当于以下显式声明：

```jldoctest parametric2
julia> struct Point{T<:Real}
           x::T
           y::T
           Point{T}(x,y) where {T<:Real} = new(x,y)
       end

julia> Point(x::T, y::T) where {T<:Real} = Point{T}(x,y);
```

注意到每个定义看起来都像它所处理的构造函数调用的形式。调用 `Point{Int64}(1,2)` 将会调用 `struct` 块内的定义 `Point{T}(x,y)`。另一方面，外部构造函数声明定义了一个适用于一般 `Point` 构造函数的方法，该方法仅适用于相同实数类型的值对。这个声明使得没有显式类型参数的构造函数调用，如 `Point(1,2)` 和 `Point(1.0,2.5)`，能够正常工作。由于方法声明限制了参数必须是相同类型，因此像 `Point(1,2.5)` 这样的调用，参数类型不同，会导致 "没有方法" 的错误。

假设我们想通过将整数值 `1` "提升" 为浮点值 `1.0` 来使构造函数调用 `Point(1,2.5)` 生效。实现这一目标的最简单方法是定义以下额外的外部构造方法：

```jldoctest parametric2
julia> Point(x::Int64, y::Float64) = Point(convert(Float64,x),y);
```

此方法使用 [`convert`](@ref) 函数显式地将 `x` 转换为 [`Float64`](@ref)，然后将构造委托给通用构造函数，以处理两个参数均为 `4d61726b646f776e2e436f64652822222c2022466c6f617436342229_40726566` 的情况。通过此方法定义，之前的 [`MethodError`](@ref) 现在成功创建了一个类型为 `Point{Float64}` 的点：

```jldoctest parametric2
julia> p = Point(1,2.5)
Point{Float64}(1.0, 2.5)

julia> typeof(p)
Point{Float64}
```

然而，其他类似的调用仍然无法正常工作：

```jldoctest parametric2
julia> Point(1.5,2)
ERROR: MethodError: no method matching Point(::Float64, ::Int64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, !Matched::T) where T<:Real
   @ Main none:1
  Point(!Matched::Int64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]
```

为了更一般地使所有此类调用正常工作，请参见 [Conversion and Promotion](@ref conversion-and-promotion)。冒着破坏悬念的风险，我们可以在这里透露，使所有对通用 `Point` 构造函数的调用按预期工作所需的只是以下外部方法定义：

```jldoctest parametric2
julia> Point(x::Real, y::Real) = Point(promote(x,y)...);
```

`promote` 函数将其所有参数转换为一种通用类型——在这种情况下是 [`Float64`](@ref)。使用这个方法定义，`Point` 构造函数以与数字运算符（如 [`+`](@ref)）相同的方式提升其参数，并适用于所有类型的实数：

```jldoctest parametric2
julia> Point(1.5,2)
Point{Float64}(1.5, 2.0)

julia> Point(1,1//2)
Point{Rational{Int64}}(1//1, 1//2)

julia> Point(1.0,1//2)
Point{Float64}(1.0, 0.5)
```

因此，尽管Julia默认提供的隐式类型参数构造函数相当严格，但可以很容易地使它们以更宽松但合理的方式运行。此外，由于构造函数可以利用类型系统、方法和多重分发的所有功能，因此定义复杂的行为通常相当简单。

## Case Study: Rational

也许将所有这些部分结合在一起的最佳方法是提供一个参数复合类型及其构造方法的真实世界示例。为此，我们实现自己的有理数类型 `OurRational`，类似于 Julia 内置的 [`Rational`](@ref) 类型，定义在 [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl)：

```jldoctest rational
julia> struct OurRational{T<:Integer} <: Real
           num::T
           den::T
           function OurRational{T}(num::T, den::T) where T<:Integer
               if num == 0 && den == 0
                    error("invalid rational: 0//0")
               end
               num = flipsign(num, den)
               den = flipsign(den, den)
               g = gcd(num, den)
               num = div(num, g)
               den = div(den, g)
               new(num, den)
           end
       end

julia> OurRational(n::T, d::T) where {T<:Integer} = OurRational{T}(n,d)
OurRational

julia> OurRational(n::Integer, d::Integer) = OurRational(promote(n,d)...)
OurRational

julia> OurRational(n::Integer) = OurRational(n,one(n))
OurRational

julia> ⊘(n::Integer, d::Integer) = OurRational(n,d)
⊘ (generic function with 1 method)

julia> ⊘(x::OurRational, y::Integer) = x.num ⊘ (x.den*y)
⊘ (generic function with 2 methods)

julia> ⊘(x::Integer, y::OurRational) = (x*y.den) ⊘ y.num
⊘ (generic function with 3 methods)

julia> ⊘(x::Complex, y::Real) = complex(real(x) ⊘ y, imag(x) ⊘ y)
⊘ (generic function with 4 methods)

julia> ⊘(x::Real, y::Complex) = (x*y') ⊘ real(y*y')
⊘ (generic function with 5 methods)

julia> function ⊘(x::Complex, y::Complex)
           xy = x*y'
           yy = real(y*y')
           complex(real(xy) ⊘ yy, imag(xy) ⊘ yy)
       end
⊘ (generic function with 6 methods)
```

第一行 – `struct OurRational{T<:Integer} <: Real` – 声明 `OurRational` 接受一个整数类型的类型参数，并且它本身是一个实数类型。字段声明 `num::T` 和 `den::T` 表示在 `OurRational{T}` 对象中保存的数据是一对类型为 `T` 的整数，一个表示有理数值的分子，另一个表示其分母。

现在事情变得有趣了。`OurRational` 有一个内部构造方法，该方法检查 `num` 和 `den` 不能同时为零，并确保每个有理数都是以“最简形式”构造的，且分母为非负数。这是通过首先在分母为负时翻转分子和分母的符号来实现的。然后，二者都被它们的最大公约数（`gcd` 总是返回一个非负数，无论其参数的符号如何）除以。因为这是 `OurRational` 唯一的内部构造函数，所以我们可以确定 `OurRational` 对象总是以这种标准化的形式构造。

`OurRational` 还提供了几个外部构造方法以方便使用。第一个是“标准”通用构造函数，当分子和分母具有相同类型时，它会从分子和分母的类型推断类型参数 `T`。第二个适用于给定的分子和分母值具有不同类型的情况：它将它们提升到一个共同类型，然后将构造委托给匹配类型参数的外部构造函数。第三个外部构造函数通过提供一个值为 `1` 的分母将整数值转换为有理数。

根据外部构造函数的定义，我们为 `⊘` 运算符定义了一些方法，这为编写有理数提供了一种语法（例如 `1 ⊘ 2`）。Julia 的 `Rational` 类型使用 [`//`](@ref) 运算符来实现这一目的。在这些定义之前，`⊘` 是一个完全未定义的运算符，仅具有语法而没有意义。之后，它的行为正如在 [Rational Numbers](@ref) 中所描述的那样——它的整个行为在这几行中得到了定义。请注意，`⊘` 的中缀用法之所以有效，是因为 Julia 有一组被识别为中缀运算符的符号。第一个也是最基本的定义使得 `a ⊘ b` 通过将 `OurRational` 构造函数应用于 `a` 和 `b` 来构造一个 `OurRational`，前提是它们是整数。当 `⊘` 的一个操作数已经是有理数时，我们稍微不同地构造结果比率的新有理数；这种行为实际上与有理数与整数的除法是相同的。最后，将 `⊘` 应用于复整数值会创建一个 `Complex{<:OurRational}` 的实例——一个其实部和虚部都是有理数的复数：

```jldoctest rational
julia> z = (1 + 2im) ⊘ (1 - 2im);

julia> typeof(z)
Complex{OurRational{Int64}}

julia> typeof(z) <: Complex{<:OurRational}
true
```

因此，尽管 `⊘` 运算符通常返回 `OurRational` 的一个实例，但如果其任一参数是复整数，它将返回 `Complex{<:OurRational}` 的一个实例。感兴趣的读者可以考虑浏览其余的 [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl)：它简短、自包含，并实现了一个完整的基本 Julia 类型。

## Outer-only constructors

正如我们所看到的，典型的参数化类型具有在已知类型参数时调用的内部构造函数；例如，它们适用于 `Point{Int}` 但不适用于 `Point`。可以选择添加外部构造函数，这些构造函数会自动确定类型参数，例如从调用 `Point(1,2)` 构造 `Point{Int}`。外部构造函数调用内部构造函数以实际创建实例。然而，在某些情况下，人们可能更愿意不提供内部构造函数，以便无法手动请求特定的类型参数。

例如，假设我们定义一个类型，该类型存储一个向量以及其和的准确表示：

```jldoctest
julia> struct SummedArray{T<:Number,S<:Number}
           data::Vector{T}
           sum::S
       end

julia> SummedArray(Int32[1; 2; 3], Int32(6))
SummedArray{Int32, Int32}(Int32[1, 2, 3], 6)
```

问题是我们希望 `S` 的类型大于 `T`，以便我们可以在信息损失较少的情况下对多个元素进行求和。例如，当 `T` 是 [`Int32`](@ref) 时，我们希望 `S` 是 [`Int64`](@ref)。因此，我们希望避免一个允许用户构造 `SummedArray{Int32,Int32}` 类型实例的接口。实现这一点的一种方法是仅为 `SummedArray` 提供构造函数，但在 `struct` 定义块内抑制默认构造函数的生成：

```jldoctest
julia> struct SummedArray{T<:Number,S<:Number}
           data::Vector{T}
           sum::S
           function SummedArray(a::Vector{T}) where T
               S = widen(T)
               new{T,S}(a, sum(S, a))
           end
       end

julia> SummedArray(Int32[1; 2; 3], Int32(6))
ERROR: MethodError: no method matching SummedArray(::Vector{Int32}, ::Int32)
The type `SummedArray` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  SummedArray(::Vector{T}) where T
   @ Main none:4

Stacktrace:
[...]
```

此构造函数将通过语法 `SummedArray(a)` 被调用。语法 `new{T,S}` 允许为要构造的类型指定参数，即此调用将返回 `SummedArray{T,S}`。`new{T,S}` 可以在任何构造函数定义中使用，但为了方便，当可能时，`new{}` 的参数会自动从正在构造的类型中推导。

## Constructors are just callable objects

任何类型的对象可以通过定义一个方法来表示为 [made callable](@ref "Function-like objects")。这包括类型，即类型为 [`Type`](@ref) 的对象；构造函数实际上可以被视为可调用的类型对象。例如，`Bool` 及其各种超类型上定义了许多方法：

```julia-repl
julia> methods(Bool)
# 10 methods for type constructor:
  [1] Bool(x::BigFloat)
     @ Base.MPFR mpfr.jl:393
  [2] Bool(x::Float16)
     @ Base float.jl:338
  [3] Bool(x::Rational)
     @ Base rational.jl:138
  [4] Bool(x::Real)
     @ Base float.jl:233
  [5] (dt::Type{<:Integer})(ip::Sockets.IPAddr)
     @ Sockets ~/tmp/jl/jl/julia-nightly-assert/share/julia/stdlib/v1.11/Sockets/src/IPAddr.jl:11
  [6] (::Type{T})(x::Enum{T2}) where {T<:Integer, T2<:Integer}
     @ Base.Enums Enums.jl:19
  [7] (::Type{T})(z::Complex) where T<:Real
     @ Base complex.jl:44
  [8] (::Type{T})(x::Base.TwicePrecision) where T<:Number
     @ Base twiceprecision.jl:265
  [9] (::Type{T})(x::T) where T<:Number
     @ boot.jl:894
 [10] (::Type{T})(x::AbstractChar) where T<:Union{AbstractChar, Number}
     @ char.jl:50
```

通常的构造函数语法与类似函数的对象语法完全等效，因此尝试使用每种语法定义方法将导致第一个方法被下一个方法覆盖：

```jldoctest
julia> struct S
           f::Int
       end

julia> S() = S(7)
S

julia> (::Type{S})() = S(8)  # overwrites the previous constructor method

julia> S()
S(8)
```
