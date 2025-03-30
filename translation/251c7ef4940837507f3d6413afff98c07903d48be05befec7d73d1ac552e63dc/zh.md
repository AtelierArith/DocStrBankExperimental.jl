# [Conversion and Promotion](@id conversion-and-promotion)

Julia 有一个系统，用于将数学运算符的参数提升到一个共同类型，这在其他多个部分中都有提到，包括 [Integers and Floating-Point Numbers](@ref)、[Mathematical Operations and Elementary Functions](@ref)、[Types](@ref man-types) 和 [Methods](@ref)。在本节中，我们将解释这个提升系统是如何工作的，以及如何将其扩展到新类型并将其应用于除内置数学运算符之外的函数。传统上，编程语言在算术参数的提升方面分为两派：

  * **内置算术类型和运算符的自动提升。** 在大多数语言中，当内置数值类型作为算术运算符的操作数使用时，例如 `+`、`-`、`*` 和 `/`，它们会自动提升为一种共同类型，以产生预期的结果。C、Java、Perl 和 Python 等语言都能正确计算 `1 + 1.5` 的和为浮点值 `2.5`，即使 `+` 的一个操作数是整数。这些系统设计得足够方便且周到，以至于对程序员来说几乎是隐形的：几乎没有人会在编写这样的表达式时有意识地想到这种提升，但编译器和解释器必须在加法之前进行转换，因为整数和浮点值不能直接相加。因此，这种自动转换的复杂规则不可避免地成为这些语言的规范和实现的一部分。
  * **没有自动提升。** 这个课程包括 Ada 和 ML - 非常“严格”的静态类型语言。在这些语言中，每个转换必须由程序员明确指定。因此，示例表达式 `1 + 1.5` 在 Ada 和 ML 中都会导致编译错误。相反，必须写成 `real(1) + 1.5`，在进行加法之前显式地将整数 `1` 转换为浮点值。然而，处处显式转换是如此不便，以至于即使是 Ada 也有一定程度的自动转换：整数字面量会自动提升到预期的整数类型，而浮点字面量也会类似地提升到适当的浮点类型。

从某种意义上说，Julia 属于“没有自动提升”类别：数学运算符只是具有特殊语法的函数，而函数的参数从不自动转换。然而，可以观察到，对各种混合参数类型应用数学运算只是多态多重分发的极端情况——这是 Julia 的分发和类型系统特别适合处理的内容。“自动”提升数学操作数只是作为一种特殊应用出现：Julia 提供了预定义的通用分发规则，用于数学运算符，当某些操作数类型的组合没有特定实现时会被调用。这些通用规则首先使用用户可定义的提升规则将所有操作数提升到一个共同类型，然后为结果值（现在是相同类型）调用相关运算符的专门实现。用户定义的类型可以通过定义转换到其他类型的方法以及提供一小部分提升规则来轻松参与此提升系统，定义在与其他类型混合时应提升到哪些类型。

## Conversion

获取某种类型 `T` 的值的标准方法是调用该类型的构造函数 `T(x)`。然而，在某些情况下，将一个值从一种类型转换为另一种类型而不需要程序员显式要求是很方便的。一个例子是将值赋给数组：如果 `A` 是一个 `Vector{Float64}`，则表达式 `A[1] = 2` 应该能够通过自动将 `2` 从 `Int` 转换为 `Float64` 并将结果存储在数组中来工作。这是通过 [`convert`](@ref) 函数完成的。

`convert` 函数通常接受两个参数：第一个是类型对象，第二个是要转换为该类型的值。返回的值是转换为给定类型实例的值。理解这个函数最简单的方法是看到它的实际应用：

```jldoctest
julia> x = 12
12

julia> typeof(x)
Int64

julia> xu = convert(UInt8, x)
0x0c

julia> typeof(xu)
UInt8

julia> xf = convert(AbstractFloat, x)
12.0

julia> typeof(xf)
Float64

julia> a = Any[1 2 3; 4 5 6]
2×3 Matrix{Any}:
 1  2  3
 4  5  6

julia> convert(Array{Float64}, a)
2×3 Matrix{Float64}:
 1.0  2.0  3.0
 4.0  5.0  6.0
```

转换并不总是可能，在这种情况下会抛出一个 [`MethodError`](@ref)，表示 `convert` 不知道如何执行请求的转换：

```jldoctest
julia> convert(AbstractFloat, "foo")
ERROR: MethodError: Cannot `convert` an object of type String to an object of type AbstractFloat
[...]
```

一些语言将将字符串解析为数字或将数字格式化为字符串视为转换（许多动态语言甚至会自动为您执行转换）。在 Julia 中情况并非如此。尽管某些字符串可以解析为数字，但大多数字符串并不是有效的数字表示，只有非常有限的子集是。因此，在 Julia 中必须使用专用的 [`parse`](@ref) 函数来执行此操作，使其更加明确。

### When is `convert` called?

以下语言构造调用 `convert`：

  * 将赋值给数组会转换为数组的元素类型。
  * 将对象的字段赋值转换为字段声明的类型。
  * 构造一个对象 [`new`](@ref) 转换为对象声明的字段类型。
  * 将带有声明类型的变量赋值（例如 `local x::T`）会转换为该类型。
  * 一个具有声明返回类型的函数将其返回值转换为该类型。
  * 将值传递给 [`ccall`](@ref) 会将其转换为相应的参数类型。

### Conversion vs. Construction

注意，`convert(T, x)` 的行为似乎与 `T(x)` 几乎相同。实际上，它通常是这样的。然而，有一个关键的语义差异：由于 `convert` 可以被隐式调用，因此它的方法仅限于被认为是“安全”或“令人意外”的情况。`convert` 只会在表示相同基本类型的事物之间进行转换（例如，不同的数字表示或不同的字符串编码）。它通常也是无损的；将一个值转换为不同类型再转换回来应该会得到完全相同的值。

有四种一般情况下构造函数与 `convert` 不同：

#### Constructors for types unrelated to their arguments

一些构造函数并不实现“转换”的概念。例如，`Timer(2)` 创建了一个 2 秒的计时器，这并不是真正的从整数到计时器的“转换”。

#### Mutable collections

`convert(T, x)` 预期返回原始的 `x`，如果 `x` 已经是类型 `T`。相反，如果 `T` 是可变集合类型，则 `T(x)` 应始终创建一个新集合（从 `x` 中复制元素）。

#### Wrapper types

对于某些类型，它们“包装”其他值，构造函数可能会将其参数包装在一个新对象中，即使它已经是请求的类型。例如，`Some(x)` 包装 `x` 以指示在结果可能是 `Some` 或 `nothing` 的上下文中存在一个值。然而，`x` 本身可能是对象 `Some(y)`，在这种情况下，结果是 `Some(Some(y))`，具有两个包装层次。另一方面，`convert(Some, x)` 将只返回 `x`，因为它已经是一个 `Some`。

#### Constructors that don't return instances of their own type

在 *非常罕见* 的情况下，构造函数 `T(x)` 可能会返回一个不是类型 `T` 的对象。这可能发生在一个包装类型是其自身的逆（例如 `Flip(Flip(x)) === x`），或者为了支持旧的调用语法以保持向后兼容性，当库被重构时。但 `convert(T, x)` 应始终返回类型 `T` 的值。

### Defining New Conversions

在定义新类型时，最初应该将所有创建它的方式定义为构造函数。如果明确隐式转换会很有用，并且某些构造函数符合上述“安全”标准，则可以添加 `convert` 方法。这些方法通常相当简单，因为它们只需要调用适当的构造函数。这样的定义可能看起来像这样：

```julia
import Base: convert
convert(::Type{MyType}, x) = MyType(x)
```

该方法的第一个参数的类型是 [`Type{MyType}`](@ref man-typet-type)，其唯一实例是 `MyType`。因此，只有在第一个参数是类型值 `MyType` 时，才会调用此方法。请注意用于第一个参数的语法：在 `::` 符号之前省略了参数名称，仅给出了类型。这是 Julia 中指定类型但不需要通过名称引用值的函数参数的语法。

所有某些抽象类型的实例默认被认为是“足够相似”的，因此在 Julia Base 中提供了一个通用的 `convert` 定义。例如，这个定义表明，通过调用一个带有 1 个参数的构造函数，将任何 `Number` 类型转换为任何其他类型是有效的：

```julia
convert(::Type{T}, x::Number) where {T<:Number} = T(x)::T
```

这意味着新的 `Number` 类型只需要定义构造函数，因为这个定义将为它们处理 `convert`。还提供了一个身份转换，以处理参数已经是请求类型的情况：

```julia
convert(::Type{T}, x::T) where {T<:Number} = x
```

类似的定义存在于 `AbstractString`、[`AbstractArray`](@ref) 和 [`AbstractDict`](@ref)。

## Promotion

推广是指将混合类型的值转换为单一的公共类型。虽然这并不是严格必要的，但通常暗示所转换的公共类型能够忠实地表示所有原始值。从这个意义上说，“推广”这个术语是合适的，因为值被转换为一种“更大”的类型——即能够在单一公共类型中表示所有输入值的类型。然而，重要的是不要将其与面向对象（结构）超类型或Julia的抽象超类型的概念混淆：推广与类型层次结构无关，而与在不同表示之间的转换有关。例如，尽管每个 [`Int32`](@ref) 值也可以表示为 [`Float64`](@ref) 值，但 `Int32` 不是 `Float64` 的子类型。

在 Julia 中，通过 [`promote`](@ref) 函数执行到一个公共“更大”类型的提升，该函数可以接受任意数量的参数，并返回相同数量的值的元组，这些值被转换为一个公共类型，或者在无法提升时抛出异常。提升的最常见用例是将数值参数转换为一个公共类型：

```jldoctest
julia> promote(1, 2.5)
(1.0, 2.5)

julia> promote(1, 2.5, 3)
(1.0, 2.5, 3.0)

julia> promote(2, 3//4)
(2//1, 3//4)

julia> promote(1, 2.5, 3, 3//4)
(1.0, 2.5, 3.0, 0.75)

julia> promote(1.5, im)
(1.5 + 0.0im, 0.0 + 1.0im)

julia> promote(1 + 2im, 3//4)
(1//1 + 2//1*im, 3//4 + 0//1*im)
```

浮点值被提升为最大的浮点参数类型。整数值被提升为最大的整数参数类型。如果类型大小相同但符号不同，则选择无符号类型。整数和浮点值的混合被提升为足够容纳所有值的浮点类型。与有理数混合的整数被提升为有理数。与浮点数混合的有理数被提升为浮点数。与实数混合的复数被提升为适当类型的复数值。

这就是使用促销的全部。其余的只是巧妙应用的问题，最典型的“巧妙”应用是定义用于数字运算的通用方法，例如算术运算符 `+`、`-`、`*` 和 `/`。以下是一些在 [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl) 中给出的通用方法定义：

```julia
+(x::Number, y::Number) = +(promote(x,y)...)
-(x::Number, y::Number) = -(promote(x,y)...)
*(x::Number, y::Number) = *(promote(x,y)...)
/(x::Number, y::Number) = /(promote(x,y)...)
```

这些方法定义表示，在没有更具体的规则来处理一对数值的加法、减法、乘法和除法时，将值提升到一个共同类型，然后再尝试一次。就这么简单：在其他地方，进行算术操作时，根本不需要担心提升到共同数值类型——这会自动发生。对于许多其他算术和数学函数，[`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl) 提供了通用的提升方法定义，但除此之外，在 Julia Base 中几乎不需要调用 `promote`。`promote` 最常见的用法出现在外部构造函数方法中，提供了便利，以允许混合类型的构造函数调用委托给内部类型，其字段提升到适当的共同类型。例如，回想一下 [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl) 提供了以下外部构造函数方法：

```julia
Rational(n::Integer, d::Integer) = Rational(promote(n,d)...)
```

这允许以下调用正常工作：

```jldoctest
julia> x = Rational(Int8(15),Int32(-5))
-3//1

julia> typeof(x)
Rational{Int32}
```

对于大多数用户定义的类型，要求程序员明确提供构造函数所需的类型是一种更好的实践，但有时，尤其是在数值问题中，自动进行类型提升可能会更方便。

### Defining Promotion Rules

尽管原则上可以直接为 `promote` 函数定义方法，但这将需要为所有可能的参数类型排列定义许多冗余的定义。相反，`promote` 的行为是通过一个名为 [`promote_rule`](@ref) 的辅助函数来定义的，可以为其提供方法。`promote_rule` 函数接受一对类型对象并返回另一个类型对象，使得参数类型的实例将被提升到返回的类型。因此，通过定义规则：

```julia
import Base: promote_rule
promote_rule(::Type{Float64}, ::Type{Float32}) = Float64
```

一个声明，当64位和32位浮点值一起提升时，它们应该提升为64位浮点数。提升类型不需要是参数类型之一。例如，以下提升规则在Julia Base中都发生：

```julia
promote_rule(::Type{BigInt}, ::Type{Float64}) = BigFloat
promote_rule(::Type{BigInt}, ::Type{Int8}) = BigInt
```

在后一种情况下，结果类型是 [`BigInt`](@ref)，因为 `BigInt` 是唯一足够大以容纳任意精度整数算术的类型。还要注意，不需要同时定义 `promote_rule(::Type{A}, ::Type{B})` 和 `promote_rule(::Type{B}, ::Type{A})`——对称性是通过 `promote_rule` 在提升过程中的使用方式隐含的。

`promote_rule` 函数被用作构建块，以定义一个名为 [`promote_type`](@ref) 的第二个函数，该函数接受任何数量的类型对象，并返回这些值作为 `promote` 的参数应该提升到的共同类型。因此，如果想要知道在没有实际值的情况下，某些类型的值集合会提升到什么类型，可以使用 `promote_type`：

```jldoctest
julia> promote_type(Int8, Int64)
Int64
```

请注意，我们**不**直接重载 `promote_type`：我们重载 `promote_rule`。`promote_type` 使用 `promote_rule`，并添加了对称性。直接重载它可能会导致歧义错误。我们重载 `promote_rule` 来定义事物应该如何被提升，并使用 `promote_type` 来查询这一点。

Internally, `promote_type` is used inside of `promote` to determine what type argument values should be converted to for promotion. The curious reader can read the code in [`promotion.jl`](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl), which defines the complete promotion mechanism in about 35 lines.

### Case Study: Rational Promotions

最后，我们完成了对朱莉亚有理数类型的持续案例研究，该类型相对复杂地使用了以下提升机制的提升规则：

```julia
import Base: promote_rule
promote_rule(::Type{Rational{T}}, ::Type{S}) where {T<:Integer,S<:Integer} = Rational{promote_type(T,S)}
promote_rule(::Type{Rational{T}}, ::Type{Rational{S}}) where {T<:Integer,S<:Integer} = Rational{promote_type(T,S)}
promote_rule(::Type{Rational{T}}, ::Type{S}) where {T<:Integer,S<:AbstractFloat} = promote_type(T,S)
```

第一条规则规定，将有理数与任何其他整数类型进行提升时，会提升为一个有理类型，其分子/分母类型是其分子/分母类型与其他整数类型提升的结果。第二条规则将相同的逻辑应用于两种不同类型的有理数，结果是它们各自的分子/分母类型的提升所形成的有理数。第三条也是最后一条规则规定，将有理数与浮点数进行提升时，结果与将分子/分母类型与浮点数进行提升的类型相同。

这小部分提升规则，加上类型的构造函数和数字的默认 `convert` 方法，足以使有理数与 Julia 的所有其他数值类型——整数、浮点数和复数——完全自然地互操作。通过以相同的方式提供适当的转换方法和提升规则，任何用户定义的数值类型都可以与 Julia 的预定义数值自然地互操作。
