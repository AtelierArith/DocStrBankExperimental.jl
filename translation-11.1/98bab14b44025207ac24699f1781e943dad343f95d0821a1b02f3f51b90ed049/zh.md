# Methods

回想一下 [Functions](@ref man-functions)，函数是一个将参数元组映射到返回值的对象，或者在无法返回适当值时抛出异常。对于不同类型的参数，相同的概念函数或操作通常会有很大的不同实现：将两个整数相加与将两个浮点数相加是非常不同的，这两者又与将一个整数与一个浮点数相加不同。尽管它们的实现有所不同，这些操作都属于“加法”的一般概念。因此，在 Julia 中，这些行为都属于一个单一的对象：`+` 函数。

为了便于平滑地使用许多不同实现相同概念的函数，函数不必一次性定义，而可以通过为某些参数类型和数量的特定组合提供特定行为来分段定义。函数的一种可能行为的定义称为*方法*。到目前为止，我们只展示了使用单一方法定义的函数示例，适用于所有类型的参数。然而，方法定义的签名可以被注释，以指示参数的类型以及数量，并且可以提供多个方法定义。当一个函数应用于特定的参数元组时，将应用最适合这些参数的特定方法。因此，函数的整体行为是其各种方法定义行为的拼接。如果这个拼接设计得当，即使方法的实现可能非常不同，函数的外部行为也会显得无缝且一致。

选择在应用函数时执行哪个方法称为 *调度*。Julia 允许调度过程根据给定的参数数量以及所有函数参数的类型来选择调用哪个函数的方法。这与传统的面向对象语言不同，在这些语言中，调度仅基于第一个参数进行，这个参数通常具有特殊的参数语法，有时是隐含的，而不是明确写作参数。[^1] 使用所有函数的参数来选择应该调用哪个方法，而不仅仅是第一个，被称为 [multiple dispatch](https://en.wikipedia.org/wiki/Multiple_dispatch)。多重调度对于数学代码特别有用，因为人为地认为操作“属于”某个参数而不是其他参数是没有意义的：在 `x + y` 中，加法操作是否更属于 `x` 而不是 `y`？数学运算符的实现通常依赖于其所有参数的类型。然而，即使超越数学运算，多重调度最终成为一种强大而方便的范式，用于构建和组织程序。

[^1]: In C++ or Java, for example, in a method call like `obj.meth(arg1,arg2)`, the object obj "receives" the method call and is implicitly passed to the method via the `this` keyword, rather than as an explicit method argument. When the current `this` object is the receiver of a method call, it can be omitted altogether, writing just `meth(arg1,arg2)`, with `this` implied as the receiving object.

!!! note
    本章中的所有示例都假设您正在为*同一*模块中的函数定义方法。如果您想为*另一个*模块中的函数添加方法，您必须`import`它或使用带有模块名称的限定名称。请参阅关于[namespace management](@ref namespace-management)的部分。


## Defining Methods

到目前为止，在我们的示例中，我们仅定义了具有不受限制参数类型的单一方法的函数。这些函数的行为就像它们在传统的动态类型语言中一样。然而，我们几乎一直在使用多重分发和方法，而没有意识到这一点：Julia 的所有标准函数和运算符，例如前面提到的 `+` 函数，都有许多方法定义它们在各种可能的参数类型和数量组合上的行为。

在定义函数时，可以选择性地限制其适用的参数类型，使用 `::` 类型断言运算符，该运算符在 [Composite Types](@ref) 部分中介绍：

```jldoctest fofxy
julia> f(x::Float64, y::Float64) = 2x + y
f (generic function with 1 method)
```

此函数定义仅适用于 `x` 和 `y` 都是类型 [`Float64`](@ref) 的值的调用：

```jldoctest fofxy
julia> f(2.0, 3.0)
7.0
```

将其应用于任何其他类型的参数将导致 [`MethodError`](@ref)：

```jldoctest fofxy
julia> f(2.0, 3)
ERROR: MethodError: no method matching f(::Float64, ::Int64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f(Float32(2.0), 3.0)
ERROR: MethodError: no method matching f(::Float32, ::Float64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Float64, ::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f(2.0, "3.0")
ERROR: MethodError: no method matching f(::Float64, ::String)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f("2.0", "3.0")
ERROR: MethodError: no method matching f(::String, ::String)
The function `f` exists, but no method is defined for this combination of argument types.
```

如您所见，参数必须严格为类型 [`Float64`](@ref)。其他数值类型，例如整数或 32 位浮点值，不会自动转换为 64 位浮点数，也不会将字符串解析为数字。由于 `Float64` 是一个具体类型，而具体类型在 Julia 中不能被子类化，因此这样的定义只能应用于完全为 `Float64` 类型的参数。然而，编写更通用的方法，其中声明的参数类型是抽象的，通常是有用的：

```jldoctest fofxy
julia> f(x::Number, y::Number) = 2x - y
f (generic function with 2 methods)

julia> f(2.0, 3)
1.0
```

此方法定义适用于任何一对参数，这些参数是 [`Number`](@ref) 的实例。它们不必是相同类型，只要它们都是数值即可。处理不同数值类型的问题被委托给表达式 `2x - y` 中的算术运算。

要定义一个具有多个方法的函数，只需多次定义该函数，使用不同数量和类型的参数。函数的第一个方法定义创建了函数对象，后续的方法定义将新方法添加到现有的函数对象中。当函数被应用时，将执行与参数的数量和类型最匹配的最具体的方法定义。因此，上述两个方法定义共同定义了 `f` 在抽象类型 `Number` 的所有实例对上的行为——但对于 [`Float64`](@ref) 值的对具有不同的特定行为。如果其中一个参数是 64 位浮点数而另一个不是，则无法调用 `f(Float64,Float64)` 方法，必须使用更通用的 `f(Number,Number)` 方法：

```jldoctest fofxy
julia> f(2.0, 3.0)
7.0

julia> f(2, 3.0)
1.0

julia> f(2.0, 3)
1.0

julia> f(2, 3)
1
```

The `2x + y` definition is only used in the first case, while the `2x - y` definition is used in the others. No automatic casting or conversion of function arguments is ever performed: all conversion in Julia is non-magical and completely explicit. [Conversion and Promotion](@ref conversion-and-promotion), however, shows how clever application of sufficiently advanced technology can be indistinguishable from magic. [^Clarke61]

对于非数值类型的值，以及少于或多于两个参数的情况，函数 `f` 仍然未定义，应用它仍将导致 [`MethodError`](@ref)：

```jldoctest fofxy
julia> f("foo", 3)
ERROR: MethodError: no method matching f(::String, ::Int64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Number, ::Number)
   @ Main none:1
  f(!Matched::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f()
ERROR: MethodError: no method matching f()
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Float64, !Matched::Float64)
   @ Main none:1
  f(!Matched::Number, !Matched::Number)
   @ Main none:1

Stacktrace:
[...]
```

您可以通过在交互式会话中输入函数对象本身，轻松查看某个函数存在的所有方法：

```jldoctest fofxy
julia> f
f (generic function with 2 methods)
```

此输出告诉我们 `f` 是一个具有两个方法的函数对象。要找出这些方法的签名，可以使用 [`methods`](@ref) 函数：

```jldoctest fofxy
julia> methods(f)
# 2 methods for generic function "f" from Main:
 [1] f(x::Float64, y::Float64)
     @ none:1
 [2] f(x::Number, y::Number)
     @ none:1
```

这表明 `f` 有两个方法，一个接受两个 `Float64` 参数，另一个接受 `Number` 类型的参数。它还指示了定义这些方法的文件和行号：因为这些方法是在 REPL 中定义的，所以我们得到的明显行号是 `none:1`。

在没有使用 `::` 的类型声明的情况下，方法参数的默认类型为 `Any`，这意味着它是无限制的，因为 Julia 中的所有值都是抽象类型 `Any` 的实例。因此，我们可以像这样为 `f` 定义一个通用方法：

```jldoctest fofxy
julia> f(x,y) = println("Whoa there, Nelly.")
f (generic function with 3 methods)

julia> methods(f)
# 3 methods for generic function "f" from Main:
 [1] f(x::Float64, y::Float64)
     @ none:1
 [2] f(x::Number, y::Number)
     @ none:1
 [3] f(x, y)
     @ none:1

julia> f("foo", 1)
Whoa there, Nelly.
```

这个通配符比任何其他可能的方法定义对于一对参数值都不够具体，因此它只会在没有其他方法定义适用的参数对上被调用。

注意，在第三个方法的签名中，参数 `x` 和 `y` 没有指定类型。这是一种简化的表达方式，等同于 `f(x::Any, y::Any)`。

尽管这似乎是一个简单的概念，但基于值类型的多重调度可能是Julia语言中最强大和最核心的特性。核心操作通常有数十种方法：

```julia-repl
julia> methods(+)
# 180 methods for generic function "+":
[1] +(x::Bool, z::Complex{Bool}) in Base at complex.jl:227
[2] +(x::Bool, y::Bool) in Base at bool.jl:89
[3] +(x::Bool) in Base at bool.jl:86
[4] +(x::Bool, y::T) where T<:AbstractFloat in Base at bool.jl:96
[5] +(x::Bool, z::Complex) in Base at complex.jl:234
[6] +(a::Float16, b::Float16) in Base at float.jl:373
[7] +(x::Float32, y::Float32) in Base at float.jl:375
[8] +(x::Float64, y::Float64) in Base at float.jl:376
[9] +(z::Complex{Bool}, x::Bool) in Base at complex.jl:228
[10] +(z::Complex{Bool}, x::Real) in Base at complex.jl:242
[11] +(x::Char, y::Integer) in Base at char.jl:40
[12] +(c::BigInt, x::BigFloat) in Base.MPFR at mpfr.jl:307
[13] +(a::BigInt, b::BigInt, c::BigInt, d::BigInt, e::BigInt) in Base.GMP at gmp.jl:392
[14] +(a::BigInt, b::BigInt, c::BigInt, d::BigInt) in Base.GMP at gmp.jl:391
[15] +(a::BigInt, b::BigInt, c::BigInt) in Base.GMP at gmp.jl:390
[16] +(x::BigInt, y::BigInt) in Base.GMP at gmp.jl:361
[17] +(x::BigInt, c::Union{UInt16, UInt32, UInt64, UInt8}) in Base.GMP at gmp.jl:398
...
[180] +(a, b, c, xs...) in Base at operators.jl:424
```

多重派发与灵活的参数类型系统结合，使得Julia能够抽象地表达与实现细节解耦的高级算法。

## [Method specializations](@id man-method-specializations)

当你创建多个相同函数的方法时，这有时被称为“特化”。在这种情况下，你通过向函数添加额外的方法来特化*函数*：每个新方法都是该函数的新特化。如上所示，这些特化由`methods`返回。

还有另一种专业化发生在没有程序员干预的情况下：Julia 的编译器可以自动针对使用的特定参数类型专门化 *方法*。这种专业化 *不会* 被 `methods` 列出，因为这并不会创建新的 `Method`，但像 [`@code_typed`](@ref) 这样的工具允许你检查这种专业化。

例如，如果您创建一个方法

```
mysum(x::Real, y::Real) = x + y
```

你给了函数 `mysum` 一个新方法（可能是它唯一的方法），而该方法接受任何一对 `Real` 数字输入。但是如果你接着执行

```julia-repl
julia> mysum(1, 2)
3

julia> mysum(1.0, 2.0)
3.0
```

Julia 将编译 `mysum` 两次，一次用于 `x::Int, y::Int`，另一次用于 `x::Float64, y::Float64`。编译两次的目的是为了性能：对于 `+`（`mysum` 使用的运算符）调用的方法会根据 `x` 和 `y` 的具体类型而有所不同，通过编译不同的特化版本，Julia 可以提前完成所有方法查找。这使得程序运行得更快，因为在运行时不必再进行方法查找。Julia 的自动特化允许你编写通用算法，并期望编译器会生成高效的特化代码来处理你所需的每种情况。

在潜在专业化的数量可能实际上是无限的情况下，Julia 可能会避免这种默认专业化。有关更多信息，请参见 [Be aware of when Julia avoids specializing](@ref)。

## [Method Ambiguities](@id man-ambiguities)

可以定义一组函数方法，使得对于某些参数组合没有唯一的最具体方法适用：

```jldoctest gofxy
julia> g(x::Float64, y) = 2x + y
g (generic function with 1 method)

julia> g(x, y::Float64) = x + 2y
g (generic function with 2 methods)

julia> g(2.0, 3)
7.0

julia> g(2, 3.0)
8.0

julia> g(2.0, 3.0)
ERROR: MethodError: g(::Float64, ::Float64) is ambiguous.

Candidates:
  g(x, y::Float64)
    @ Main none:1
  g(x::Float64, y)
    @ Main none:1

Possible fix, define
  g(::Float64, ::Float64)

Stacktrace:
[...]
```

在这里，调用 `g(2.0, 3.0)` 可以由 `g(::Float64, ::Any)` 或 `g(::Any, ::Float64)` 方法处理。方法的定义顺序并不重要，且两者都不比另一方更具体。在这种情况下，Julia 会引发一个 [`MethodError`](@ref)，而不是任意选择一个方法。您可以通过为交集情况指定适当的方法来避免方法歧义：

```jldoctest gofxy
julia> g(x::Float64, y::Float64) = 2x + 2y
g (generic function with 3 methods)

julia> g(2.0, 3)
7.0

julia> g(2, 3.0)
8.0

julia> g(2.0, 3.0)
10.0
```

建议首先定义消歧义方法，因为否则在更具体的方法被定义之前，模糊性会存在，即使是暂时的。

在更复杂的情况下，解决方法的模糊性涉及一定的设计元素；这个主题在 [below](@ref man-method-design-ambiguities) 中进一步探讨。

## Parametric Methods

方法定义可以选择性地具有类型参数来限定签名：

```jldoctest same_typefunc
julia> same_type(x::T, y::T) where {T} = true
same_type (generic function with 1 method)

julia> same_type(x,y) = false
same_type (generic function with 2 methods)
```

第一种方法适用于两个参数都是相同具体类型的情况，无论该类型是什么，而第二种方法则作为一个通用方法，涵盖所有其他情况。因此，总体而言，这定义了一个布尔函数，用于检查其两个参数是否属于相同类型：

```jldoctest same_typefunc
julia> same_type(1, 2)
true

julia> same_type(1, 2.0)
false

julia> same_type(1.0, 2.0)
true

julia> same_type("foo", 2.0)
false

julia> same_type("foo", "bar")
true

julia> same_type(Int32(1), Int64(2))
false
```

这样的定义对应于类型签名为 `UnionAll` 类型的方法（见 [UnionAll Types](@ref)）。

这种通过调度定义函数行为的方式在 Julia 中相当常见，甚至可以说是惯用法。方法类型参数不仅限于作为参数的类型使用：它们可以在函数签名或函数体中任何值的位置使用。以下是一个示例，其中方法类型参数 `T` 被用作方法签名中参数化类型 `Vector{T}` 的类型参数：

```jldoctest
julia> function myappend(v::Vector{T}, x::T) where {T}
           return [v..., x]
       end
myappend (generic function with 1 method)
```

类型参数 `T` 在这个例子中确保添加的元素 `x` 是向量 `v` 的现有元素类型的子类型。`where` 关键字在方法签名定义后引入这些约束的列表。这对于如上所示的一行定义同样适用，并且必须出现在 [return type declaration](@ref man-functions-return-type) 之前（如果存在），如下所示：

```jldoctest
julia> (myappend(v::Vector{T}, x::T)::Vector) where {T} = [v..., x]
myappend (generic function with 1 method)

julia> myappend([1,2,3],4)
4-element Vector{Int64}:
 1
 2
 3
 4

julia> myappend([1,2,3],2.5)
ERROR: MethodError: no method matching myappend(::Vector{Int64}, ::Float64)
The function `myappend` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  myappend(::Vector{T}, !Matched::T) where T
   @ Main none:1

Stacktrace:
[...]

julia> myappend([1.0,2.0,3.0],4.0)
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0

julia> myappend([1.0,2.0,3.0],4)
ERROR: MethodError: no method matching myappend(::Vector{Float64}, ::Int64)
The function `myappend` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  myappend(::Vector{T}, !Matched::T) where T
   @ Main none:1

Stacktrace:
[...]
```

如果附加元素的类型与其附加到的向量的元素类型不匹配，则会引发 [`MethodError`](@ref)。在以下示例中，方法的类型参数 `T` 被用作返回值：

```jldoctest
julia> mytypeof(x::T) where {T} = T
mytypeof (generic function with 1 method)

julia> mytypeof(1)
Int64

julia> mytypeof(1.0)
Float64
```

正如您可以在类型声明中对类型参数施加子类型约束（参见 [Parametric Types](@ref)），您也可以对方法的类型参数施加约束：

```jldoctest
julia> same_type_numeric(x::T, y::T) where {T<:Number} = true
same_type_numeric (generic function with 1 method)

julia> same_type_numeric(x::Number, y::Number) = false
same_type_numeric (generic function with 2 methods)

julia> same_type_numeric(1, 2)
true

julia> same_type_numeric(1, 2.0)
false

julia> same_type_numeric(1.0, 2.0)
true

julia> same_type_numeric("foo", 2.0)
ERROR: MethodError: no method matching same_type_numeric(::String, ::Float64)
The function `same_type_numeric` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  same_type_numeric(!Matched::T, ::T) where T<:Number
   @ Main none:1
  same_type_numeric(!Matched::Number, ::Number)
   @ Main none:1

Stacktrace:
[...]

julia> same_type_numeric("foo", "bar")
ERROR: MethodError: no method matching same_type_numeric(::String, ::String)
The function `same_type_numeric` exists, but no method is defined for this combination of argument types.

julia> same_type_numeric(Int32(1), Int64(2))
false
```

`same_type_numeric` 函数的行为与上面定义的 `same_type` 函数非常相似，但仅适用于数字对。

参数化方法允许与用于编写类型的 `where` 表达式相同的语法（参见 [UnionAll Types](@ref)）。如果只有一个参数，则可以省略外部的大括号（在 `where {T}` 中），但通常为了清晰起见，还是更倾向于保留。多个参数可以用逗号分隔，例如 `where {T, S<:Real}`，或者使用嵌套的 `where` 来书写，例如 `where S<:Real where T`。

## Redefining Methods

当重新定义一个方法或添加新方法时，重要的是要意识到这些更改不会立即生效。这是朱莉亚能够静态推断和编译代码以快速运行的关键，而不需要通常的 JIT 技巧和开销。实际上，任何新的方法定义在当前运行时环境中都是不可见的，包括任务和线程（以及任何先前定义的 `@generated` 函数）。让我们从一个例子开始，看看这意味着什么：

```julia-repl
julia> function tryeval()
           @eval newfun() = 1
           newfun()
       end
tryeval (generic function with 1 method)

julia> tryeval()
ERROR: MethodError: no method matching newfun()
The applicable method may be too new: running in world age xxxx1, while current world is xxxx2.
Closest candidates are:
  newfun() at none:1 (method too new to be called from this world context.)
 in tryeval() at none:1
 ...

julia> newfun()
1
```

在这个例子中，注意到新的 `newfun` 定义已经创建，但无法立即调用。新的全局变量对 `tryeval` 函数是立即可见的，因此你可以写 `return newfun`（不带括号）。但是你、你的调用者、他们调用的函数等都无法调用这个新的方法定义！

但有一个例外：从 REPL 调用 `newfun` 的未来调用按预期工作，能够看到并调用 `newfun` 的新定义。

然而，未来对 `tryeval` 的调用将继续看到 `newfun` 的定义，正如它在 REPL 中的 *上一个语句* 一样，因此在对 `tryeval` 的调用之前。

您可能想亲自尝试一下，以了解它是如何工作的。

该行为的实现是一个“世界年龄计数器”。这个单调递增的值跟踪每个方法定义操作。这允许将“可被给定运行时环境看到的方法定义集合”描述为一个单一的数字，或称为“世界年龄”。它还允许通过比较它们的序数值来比较两个世界中可用的方法。在上面的例子中，我们看到“当前世界”（其中存在方法`newfun`）比在执行`tryeval`开始时固定的任务本地“运行时世界”大一。

有时需要绕过这个（例如，如果您正在实现上述 REPL）。幸运的是，有一个简单的解决方案：使用 [`Base.invokelatest`](@ref) 调用该函数：

```jldoctest
julia> function tryeval2()
           @eval newfun2() = 2
           Base.invokelatest(newfun2)
       end
tryeval2 (generic function with 1 method)

julia> tryeval2()
2
```

最后，让我们看看一些更复杂的例子，在这些例子中，这条规则发挥作用。定义一个函数 `f(x)`，它最初有一个方法：

```jldoctest redefinemethod
julia> f(x) = "original definition"
f (generic function with 1 method)
```

开始一些其他使用 `f(x)` 的操作：

```jldoctest redefinemethod
julia> g(x) = f(x)
g (generic function with 1 method)

julia> t = @async f(wait()); yield();
```

现在我们为 `f(x)` 添加一些新方法：

```jldoctest redefinemethod
julia> f(x::Int) = "definition for Int"
f (generic function with 2 methods)

julia> f(x::Type{Int}) = "definition for Type{Int}"
f (generic function with 3 methods)
```

比较这些结果的不同之处：

```jldoctest redefinemethod
julia> f(1)
"definition for Int"

julia> g(1)
"definition for Int"

julia> fetch(schedule(t, 1))
"original definition"

julia> t = @async f(wait()); yield();

julia> fetch(schedule(t, 1))
"definition for Int"
```

## Design Patterns with Parametric Methods

虽然复杂的调度逻辑对于性能或可用性并不是必需的，但有时它可以是表达某些算法的最佳方式。以下是一些在以这种方式使用调度时常见的设计模式。

### Extracting the type parameter from a super-type

这是一个正确的代码模板，用于返回任何具有明确定义元素类型的 `AbstractArray` 任意子类型的元素类型 `T`：

```julia
abstract type AbstractArray{T, N} end
eltype(::Type{<:AbstractArray{T}}) where {T} = T
```

使用所谓的三角调度。请注意，`UnionAll` 类型，例如 `eltype(AbstractArray{T} where T <: Integer)`，不匹配上述方法。`Base` 中的 `eltype` 实现为这种情况添加了一个对 `Any` 的后备方法。

一个常见的错误是试图通过使用反射来获取元素类型：

```julia
eltype_wrong(::Type{A}) where {A<:AbstractArray} = A.parameters[1]
```

然而，构造出这种情况失败的例子并不难：

```julia
struct BitVector <: AbstractArray{Bool, 1}; end
```

在这里，我们创建了一个类型 `BitVector`，它没有参数，但元素类型仍然完全指定，其中 `T` 等于 `Bool`！

另一个错误是尝试使用 `supertype` 向上遍历类型层次结构：

```julia
eltype_wrong(::Type{AbstractArray{T}}) where {T} = T
eltype_wrong(::Type{AbstractArray{T, N}}) where {T, N} = T
eltype_wrong(::Type{A}) where {A<:AbstractArray} = eltype_wrong(supertype(A))
```

虽然这对声明的类型有效，但对于没有超类型的类型则无效：

```julia-repl
julia> eltype_wrong(Union{AbstractArray{Int}, AbstractArray{Float64}})
ERROR: MethodError: no method matching supertype(::Type{Union{AbstractArray{Float64,N} where N, AbstractArray{Int64,N} where N}})
Closest candidates are:
  supertype(::DataType) at operators.jl:43
  supertype(::UnionAll) at operators.jl:48
```

### Building a similar type with a different type parameter

在构建通用代码时，通常需要构造一个类似的对象，并对类型的布局进行一些更改，这也需要更改类型参数。例如，您可能有某种抽象数组，具有任意元素类型，并希望使用特定元素类型在其上进行计算。我们必须为每个 `AbstractArray{T}` 子类型实现一个方法，描述如何计算这种类型转换。没有将一个子类型一般转换为另一个具有不同参数的子类型的方法。

`AbstractArray` 的子类型通常实现两个方法来实现这一点：一个方法将输入数组转换为特定 `AbstractArray{T, N}` 抽象类型的子类型；另一个方法创建一个具有特定元素类型的新未初始化数组。这些方法的示例实现可以在 Julia Base 中找到。以下是它们的基本用法示例，确保 `input` 和 `output` 是相同类型：

```julia
input = convert(AbstractArray{Eltype}, input)
output = similar(input, Eltype)
```

作为此内容的扩展，在算法需要输入数组的副本的情况下，[`convert`](@ref) 是不够的，因为返回值可能与原始输入别名。结合 [`similar`](@ref)（以生成输出数组）和 [`copyto!`](@ref)（以填充输入数据）是一种通用方式来表达对输入参数可变副本的要求：

```julia
copy_with_eltype(input, Eltype) = copyto!(similar(input, Eltype), input)
```

### Iterated dispatch

为了调度多级参数列表，通常最好将每个调度级别分成不同的函数。这听起来与单一调度的方法相似，但正如我们下面将看到的，它仍然更加灵活。

例如，尝试在数组的元素类型上进行调度通常会遇到模糊的情况。相反，通常代码会首先在容器类型上进行调度，然后根据元素类型递归到更具体的方法。在大多数情况下，算法方便地适应这种层次化的方法，而在其他情况下，这种严格性必须手动解决。这种调度分支可以在例如求和两个矩阵的逻辑中观察到：

```julia
# First dispatch selects the map algorithm for element-wise summation.
+(a::Matrix, b::Matrix) = map(+, a, b)
# Then dispatch handles each element and selects the appropriate
# common element type for the computation.
+(a, b) = +(promote(a, b)...)
# Once the elements have the same type, they can be added.
# For example, via primitive operations exposed by the processor.
+(a::Float64, b::Float64) = Core.add(a, b)
```

### Trait-based dispatch

一个自然的扩展是为上述迭代调度添加一个方法选择层，允许在与类型层次结构定义的集合独立的类型集合上进行调度。我们可以通过写出相关类型的 `Union` 来构造这样的集合，但这样一来，该集合就无法扩展，因为 `Union` 类型在创建后无法更改。然而，可以通过一种通常称为 ["Holy-trait"](https://github.com/JuliaLang/julia/issues/2345#issuecomment-54537633) 的设计模式来编程实现这样一个可扩展的集合。

此模式通过定义一个通用函数来实现，该函数为每个可能属于的特征集计算不同的单例值（或类型）。如果该函数是纯粹的，与正常调度相比，对性能没有影响。

在上一节的示例中，略过了 [`map`](@ref) 和 [`promote`](@ref) 的实现细节，这两个都基于这些特性进行操作。当遍历矩阵时，例如在 `map` 的实现中，一个重要的问题是使用什么顺序来遍历数据。当 `AbstractArray` 子类型实现 [`Base.IndexStyle`](@ref) 特性时，其他函数如 `map` 可以根据这些信息进行调度，以选择最佳算法（参见 [Abstract Array Interface](@ref man-interface-array)）。这意味着每个子类型不需要实现自定义版本的 `map`，因为通用定义 + 特性类将使系统能够选择最快的版本。以下是一个基于特性的 `map` 玩具实现：

```julia
map(f, a::AbstractArray, b::AbstractArray) = map(Base.IndexStyle(a, b), f, a, b)
# generic implementation:
map(::Base.IndexCartesian, f, a::AbstractArray, b::AbstractArray) = ...
# linear-indexing implementation (faster)
map(::Base.IndexLinear, f, a::AbstractArray, b::AbstractArray) = ...
```

这种基于特征的方法也存在于 [`promote`](@ref) 机制中，该机制由标量 `+` 使用。它使用 [`promote_type`](@ref)，该机制返回用于计算操作的最佳公共类型，考虑到操作数的两种类型。这使得将为每对可能的类型参数实现每个函数的问题，简化为从每种类型到公共类型的转换操作的问题，加上一个首选成对提升规则的表。

### Output-type computation

基于特征的提升讨论为我们下一个设计模式提供了过渡：计算矩阵操作的输出元素类型。

为了实现基本操作，例如加法，我们使用 [`promote_type`](@ref) 函数来计算所需的输出类型。（和之前一样，我们在对 `+` 的调用中的 `promote` 调用中看到了这一点）。

对于矩阵上的更复杂函数，可能需要计算更复杂操作序列的预期返回类型。这通常通过以下步骤进行：

1. Write a small function `op` that expresses the set of operations performed by the kernel of the algorithm.
2. 计算结果矩阵的元素类型 `R` 为 `promote_op(op, argument_types...)`，其中 `argument_types` 是通过对每个输入数组应用 `eltype` 计算得出的。
3. 构建输出矩阵为 `similar(R, dims)`，其中 `dims` 是输出数组的期望维度。

对于一个更具体的例子，一个通用的方阵乘法伪代码可能如下所示：

```julia
function matmul(a::AbstractMatrix, b::AbstractMatrix)
    op = (ai, bi) -> ai * bi + ai * bi

    ## this is insufficient because it assumes `one(eltype(a))` is constructable:
    # R = typeof(op(one(eltype(a)), one(eltype(b))))

    ## this fails because it assumes `a[1]` exists and is representative of all elements of the array
    # R = typeof(op(a[1], b[1]))

    ## this is incorrect because it assumes that `+` calls `promote_type`
    ## but this is not true for some types, such as Bool:
    # R = promote_type(ai, bi)

    # this is wrong, since depending on the return value
    # of type-inference is very brittle (as well as not being optimizable):
    # R = Base.return_types(op, (eltype(a), eltype(b)))

    ## but, finally, this works:
    R = promote_op(op, eltype(a), eltype(b))
    ## although sometimes it may give a larger type than desired
    ## it will always give a correct type

    output = similar(b, R, (size(a, 1), size(b, 2)))
    if size(a, 2) > 0
        for j in 1:size(b, 2)
            for i in 1:size(a, 1)
                ## here we don't use `ab = zero(R)`,
                ## since `R` might be `Any` and `zero(Any)` is not defined
                ## we also must declare `ab::R` to make the type of `ab` constant in the loop,
                ## since it is possible that typeof(a * b) != typeof(a * b + a * b) == R
                ab::R = a[i, 1] * b[1, j]
                for k in 2:size(a, 2)
                    ab += a[i, k] * b[k, j]
                end
                output[i, j] = ab
            end
        end
    end
    return output
end
```

### Separate convert and kernel logic

一种显著减少编译时间和测试复杂性的方式是将转换为所需类型的逻辑与计算逻辑隔离。这使得编译器能够独立于更大内核的其余部分对转换逻辑进行特化和内联。

这是在将较大类型类转换为算法实际支持的特定参数类型时常见的模式：

```julia
complexfunction(arg::Int) = ...
complexfunction(arg::Any) = complexfunction(convert(Int, arg))

matmul(a::T, b::T) = ...
matmul(a, b) = matmul(promote(a, b)...)
```

## Parametrically-constrained Varargs methods

函数参数也可以用来限制可以提供给“可变参数”函数的参数数量 ([Varargs Functions](@ref))。 记号 `Vararg{T,N}` 用于表示这样的约束。 例如：

```jldoctest
julia> bar(a,b,x::Vararg{Any,2}) = (a,b,x)
bar (generic function with 1 method)

julia> bar(1,2,3)
ERROR: MethodError: no method matching bar(::Int64, ::Int64, ::Int64)
The function `bar` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  bar(::Any, ::Any, ::Any, !Matched::Any)
   @ Main none:1

Stacktrace:
[...]

julia> bar(1,2,3,4)
(1, 2, (3, 4))

julia> bar(1,2,3,4,5)
ERROR: MethodError: no method matching bar(::Int64, ::Int64, ::Int64, ::Int64, ::Int64)
The function `bar` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  bar(::Any, ::Any, ::Any, ::Any)
   @ Main none:1

Stacktrace:
[...]
```

更有用的是，可以通过参数来限制可变参数方法。例如：

```julia
function getindex(A::AbstractArray{T,N}, indices::Vararg{Number,N}) where {T,N}
```

仅在 `indices` 的数量与数组的维度匹配时才会被调用。

当仅需要限制提供的参数类型时，`Vararg{T}` 可以等效地写为 `T...`。例如，`f(x::Int...) = x` 是 `f(x::Vararg{Int}) = x` 的简写。

## Note on Optional and keyword Arguments

如在 [Functions](@ref man-functions) 中简要提到的，可选参数作为多重方法定义的语法实现。例如，这个定义：

```julia
f(a=1,b=2) = a+2b
```

翻译为以下三种方法：

```julia
f(a,b) = a+2b
f(a) = f(a,2)
f() = f(1,2)
```

这意味着调用 `f()` 等同于调用 `f(1,2)`。在这种情况下，结果是 `5`，因为 `f(1,2)` 调用了上面 `f` 的第一个方法。然而，这并不总是如此。如果你定义一个更专门针对整数的第四个方法：

```julia
f(a::Int,b::Int) = a-2b
```

然后 `f()` 和 `f(1,2)` 的结果都是 `-3`。换句话说，可选参数与函数相关，而不是与该函数的任何特定方法相关。调用哪个方法取决于可选参数的类型。当可选参数以全局变量的形式定义时，可选参数的类型甚至可能在运行时发生变化。

关键字参数的行为与普通位置参数有很大不同。特别是，它们不参与方法调度。方法的调度仅基于位置参数，关键字参数在匹配的方法被识别后才会被处理。

## Function-like objects

方法与类型相关联，因此可以通过向其类型添加方法，使任何任意的 Julia 对象变得“可调用”。（这种“可调用”的对象有时被称为“函子”。）

例如，您可以定义一个类型来存储多项式的系数，但它的行为像一个评估多项式的函数：

```jldoctest polynomial
julia> struct Polynomial{R}
           coeffs::Vector{R}
       end

julia> function (p::Polynomial)(x)
           v = p.coeffs[end]
           for i = (length(p.coeffs)-1):-1:1
               v = v*x + p.coeffs[i]
           end
           return v
       end

julia> (p::Polynomial)() = p(5)
```

注意到该函数是通过类型而不是名称来指定的。与普通函数一样，有一种简洁的语法形式。在函数体内，`p` 将引用被调用的对象。`Polynomial` 可以如下使用：

```jldoctest polynomial
julia> p = Polynomial([1,10,100])
Polynomial{Int64}([1, 10, 100])

julia> p(3)
931

julia> p()
2551
```

这个机制也是类型构造函数和闭包（引用其周围环境的内部函数）在Julia中如何工作的关键。

## Empty generic functions

有时引入一个通用函数而不添加方法是有用的。这可以用来将接口定义与实现分开。这样做也可能是出于文档或代码可读性的目的。其语法是一个空的 `function` 块，没有参数元组：

```julia
function emptyfunc end
```

## [Method design and the avoidance of ambiguities](@id man-method-design-ambiguities)

Julia 的方法多态性是其最强大的特性之一，但利用这一能力可能会带来设计挑战。特别是在更复杂的方法层次结构中，出现 [ambiguities](@ref man-ambiguities) 是很常见的。

上面提到，可以通过以下方式解决歧义：

```julia
f(x, y::Int) = 1
f(x::Int, y) = 2
```

通过定义一个方法

```julia
f(x::Int, y::Int) = 3
```

这通常是正确的策略；然而，在某些情况下，盲目遵循这一建议可能会适得其反。特别是，当一个通用函数拥有更多的方法时，模糊性的可能性就会增加。当你的方法层次结构比这个简单的例子更复杂时，仔细考虑替代策略可能会对你有所帮助。

以下我们讨论了特定的挑战以及一些解决这些问题的替代方法。

### Tuple and NTuple arguments

`Tuple`（和 `NTuple`）参数带来了特殊的挑战。例如，

```julia
f(x::NTuple{N,Int}) where {N} = 1
f(x::NTuple{N,Float64}) where {N} = 2
```

因为存在 `N == 0` 的可能性而变得模糊：没有元素来确定应该调用 `Int` 还是 `Float64` 变体。为了解决这种模糊性，一种方法是为空元组定义一个方法：

```julia
f(x::Tuple{}) = 3
```

或者，对于所有方法（但有一个例外），您可以坚持认为元组中至少有一个元素：

```julia
f(x::NTuple{N,Int}) where {N} = 1           # this is the fallback
f(x::Tuple{Float64, Vararg{Float64}}) = 2   # this requires at least one Float64
```

### [Orthogonalize your design](@id man-methods-orthogonalize)

当你可能会想要对两个或更多参数进行调度时，考虑一下“包装”函数是否可以使设计更简单。例如，代替编写多个变体：

```julia
f(x::A, y::A) = ...
f(x::A, y::B) = ...
f(x::B, y::A) = ...
f(x::B, y::B) = ...
```

你可能考虑定义

```julia
f(x::A, y::A) = ...
f(x, y) = f(g(x), g(y))
```

其中 `g` 将参数转换为类型 `A`。这是更一般原则的一个非常具体的例子，即 [orthogonal design](https://en.wikipedia.org/wiki/Orthogonality_(programming))，在这个原则中，独立的概念被分配给独立的方法。在这里，`g` 很可能需要一个后备定义。

```julia
g(x::A) = x
```

一个相关的策略利用 `promote` 将 `x` 和 `y` 提升到一个共同的类型：

```julia
f(x::T, y::T) where {T} = ...
f(x, y) = f(promote(x, y)...)
```

这种设计的一个风险是，如果没有合适的促销方法将 `x` 和 `y` 转换为相同类型，第二种方法将无限递归自身并触发堆栈溢出。

### Dispatch on one argument at a time

如果您需要在多个参数上进行分发，并且有许多后备选项，组合太多以至于不切实际地定义所有可能的变体，那么可以考虑引入“名称级联”，例如，您可以在第一个参数上进行分发，然后调用一个内部方法：

```julia
f(x::A, y) = _fA(x, y)
f(x::B, y) = _fB(x, y)
```

然后内部方法 `_fA` 和 `_fB` 可以在 `y` 上进行调度，而不必担心与彼此在 `x` 上的歧义。

请注意，这种策略至少有一个主要缺点：在许多情况下，用户无法通过定义您导出函数 `f` 的进一步特化来进一步自定义 `f` 的行为。相反，他们必须为您的内部方法 `_fA` 和 `_fB` 定义特化，这模糊了导出方法和内部方法之间的界限。

### Abstract containers and element types

尽可能避免定义针对抽象容器特定元素类型的调度方法。例如，

```julia
-(A::AbstractArray{T}, b::Date) where {T<:Date}
```

为任何定义方法的人生成歧义

```julia
-(A::MyArrayType{T}, b::T) where {T}
```

最佳的方法是避免定义这两种方法中的*任何一种*：相反，依赖于一个通用方法 `-(A::AbstractArray, b)`，并确保这个方法是通过通用调用（如 `similar` 和 `-`）实现的，这样可以针对每种容器类型和元素类型*单独*执行正确的操作。这只是对建议的一个更复杂的变体，即 [orthogonalize](@ref man-methods-orthogonalize) 你的方法。

当这种方法不可行时，可能值得与其他开发人员讨论解决歧义的问题；仅仅因为一种方法是首先定义的，并不意味着它不能被修改或消除。作为最后的手段，一位开发人员可以定义“权宜之计”方法。

```julia
-(A::MyArrayType{T}, b::Date) where {T<:Date} = ...
```

这通过暴力解决了歧义。

### Complex method "cascades" with default arguments

如果您正在定义一个提供默认值的方法“cascade”，请注意不要丢弃任何对应于潜在默认值的参数。例如，假设您正在编写一个数字滤波算法，并且您有一个通过应用填充来处理信号边缘的方法：

```julia
function myfilter(A, kernel, ::Replicate)
    Apadded = replicate_edges(A, size(kernel))
    myfilter(Apadded, kernel)  # now perform the "real" computation
end
```

这将违反提供默认填充的方法：

```julia
myfilter(A, kernel) = myfilter(A, kernel, Replicate()) # replicate the edge by default
```

这两种方法一起生成了一个无限递归，`A` 不断变得更大。

更好的设计是将您的调用层次结构定义如下：

```julia
struct NoPad end  # indicate that no padding is desired, or that it's already applied

myfilter(A, kernel) = myfilter(A, kernel, Replicate())  # default boundary conditions

function myfilter(A, kernel, ::Replicate)
    Apadded = replicate_edges(A, size(kernel))
    myfilter(Apadded, kernel, NoPad())  # indicate the new boundary conditions
end

# other padding methods go here

function myfilter(A, kernel, ::NoPad)
    # Here's the "real" implementation of the core computation
end
```

`NoPad` 在与其他类型的填充相同的参数位置中提供，因此它保持了调度层次结构的良好组织，并减少了歧义的可能性。此外，它扩展了“公共” `myfilter` 接口：希望显式控制填充的用户可以直接调用 `NoPad` 变体。

## Defining methods in local scope

您可以在一个 [local scope](@ref scope-of-variables) 中定义方法，例如

```jldoctest
julia> function f(x)
           g(y::Int) = y + x
           g(y) = y - x
           g
       end
f (generic function with 1 method)

julia> h = f(3);

julia> h(4)
7

julia> h(4.0)
1.0
```

然而，您*不应*有条件地或根据控制流定义局部方法，如在

```julia
function f2(inc)
    if inc
        g(x) = x + 1
    else
        g(x) = x - 1
    end
end

function f3()
    function g end
    return g
    g() = 0
end
```

由于尚不清楚最终将定义什么函数，将来以这种方式定义局部方法可能会导致错误。

对于这种情况，请改用匿名函数：

```julia
function f2(inc)
    g = if inc
        x -> x + 1
    else
        x -> x - 1
    end
end
```

[^Clarke61]: Arthur C. Clarke, *Profiles of the Future* (1961): Clarke's Third Law.
