# [Functions](@id man-functions)

在Julia中，函数是一个将参数值元组映射到返回值的对象。Julia函数不是纯粹的数学函数，因为它们可以改变并受到程序全局状态的影响。在Julia中定义函数的基本语法是：

```jldoctest
julia> function f(x, y)
           x + y
       end
f (generic function with 1 method)
```

此函数接受两个参数 `x` 和 `y`，并返回最后一个被评估的表达式的值，即 `x + y`。

在Julia中，有一种更简洁的语法来定义函数。上面演示的传统函数声明语法等价于以下紧凑的“赋值形式”：

```jldoctest fofxy
julia> f(x, y) = x + y
f (generic function with 1 method)
```

在赋值形式中，函数的主体必须是一个单一的表达式，尽管它可以是一个复合表达式（参见 [Compound Expressions](@ref man-compound-expressions)）。在Julia中，简短、简单的函数定义是很常见的。因此，简短的函数语法相当符合习惯，显著减少了输入和视觉噪音。

一个函数使用传统的括号语法被调用：

```jldoctest fofxy
julia> f(2, 3)
5
```

没有括号时，表达式 `f` 指的是函数对象，可以像其他值一样传递。

```jldoctest fofxy
julia> g = f;

julia> g(2, 3)
5
```

与变量一样，Unicode 也可以用于函数名称：

```jldoctest
julia> ∑(x, y) = x + y
∑ (generic function with 1 method)

julia> ∑(2, 3)
5
```

## [Argument Passing Behavior](@id man-argument-passing)

Julia 函数参数遵循一种有时称为“共享传递”的约定，这意味着在传递给函数时不会复制值。函数参数本身充当新的变量 *绑定*（新的“名称”可以引用值），就像 [assignments](@ref man-assignment-expressions) `argument_name = argument_value`，因此它们所引用的对象与传递的值是相同的。在函数内部对可变值（例如 `Array`）所做的修改将对调用者可见。（这与 Scheme、大多数 Lisp、Python、Ruby 和 Perl 等其他动态语言中的行为相同。）

例如，在函数中

```julia
function f(x, y)
    x[1] = 42    # mutates x
    y = 7 + y    # new binding for y, no mutation
    return y
end
```

语句 `x[1] = 42` *改变* 了对象 `x`，因此这个变化 *将* 在调用者为此参数传递的数组中可见。另一方面，赋值 `y = 7 + y` 将 *绑定* （“名称”）`y` 更改为引用一个新值 `7 + y`，而不是改变 `y` 所引用的 *原始* 对象，因此并 *不* 改变调用者传递的相应参数。这可以通过调用 `f(x, y)` 来观察：

```julia-repl
julia> a = [4, 5, 6]
3-element Vector{Int64}:
 4
 5
 6

julia> b = 3
3

julia> f(a, b) # returns 7 + b == 10
10

julia> a  # a[1] is changed to 42 by f
3-element Vector{Int64}:
 42
  5
  6

julia> b  # not changed
3
```

作为 Julia 中的一个常见约定（不是语法要求），这样的函数会 [typically be named `f!(x, y)`](@ref man-punctuation) 而不是 `f(x, y)`，作为在调用位置的视觉提醒，至少有一个参数（通常是第一个）正在被修改。

!!! warning "Shared memory between arguments"
    当一个被修改的参数与另一个参数共享内存时，变异函数的行为可能会出乎意料，这种情况称为别名（例如，当一个是另一个的视图时）。除非函数文档字符串明确指出别名会产生预期结果，否则调用者有责任确保在此类输入上的正确行为。


## Argument-type declarations

您可以通过在参数名称后附加 `::TypeName` 来声明函数参数的类型，正如在 Julia 中对 [Type Declarations](@ref) 的常规做法。例如，以下函数递归地计算 [Fibonacci numbers](https://en.wikipedia.org/wiki/Fibonacci_number)：

```
fib(n::Integer) = n ≤ 2 ? one(n) : fib(n-1) + fib(n-2)
```

并且 `::Integer` 规范意味着只有当 `n` 是 [abstract](@ref man-abstract-types) `Integer` 类型的子类型时，它才会被调用。

参数类型声明 **通常对性能没有影响**：无论声明了什么参数类型（如果有的话），Julia 都会为调用者传递的实际参数类型编译一个专门版本的函数。例如，调用 `fib(1)` 将触发为 `Int` 参数专门优化的 `fib` 的编译版本，这个版本在调用 `fib(7)` 或 `fib(15)` 时会被重用。（在某些罕见情况下，参数类型声明可能会触发额外的编译器专门化；请参见： [Be aware of when Julia avoids specializing](@ref)。） 在 Julia 中声明参数类型的最常见原因是：

  * **调度：** 如在 [Methods](@ref) 中所解释的，您可以为不同的参数类型拥有不同版本（“方法”）的函数，在这种情况下，参数类型用于确定为哪些参数调用哪个实现。例如，您可能会实现一个完全不同的算法 `fib(x::Number) = ...`，该算法适用于任何 `Number` 类型，通过使用 [Binet's formula](https://en.wikipedia.org/wiki/Fibonacci_number#Binet%27s_formula) 将其扩展到非整数值。
  * **正确性：** 如果您的函数仅对某些参数类型返回正确结果，则类型声明可能会很有用。例如，如果我们省略参数类型并写成 `fib(n) = n ≤ 2 ? one(n) : fib(n-1) + fib(n-2)`，那么 `fib(1.5)` 将默默地给出无意义的答案 `1.0`。
  * **清晰度：** 类型声明可以作为关于预期参数的文档形式。

然而，**过度限制参数类型是一个常见错误**，这可能不必要地限制函数的适用性，并阻止它在你未预料到的情况下被重用。例如，上面的 `fib(n::Integer)` 函数对于 `Int` 参数（机器整数）和 `BigInt` 任意精度整数同样有效（见 [BigFloats and BigInts](@ref BigFloats-and-BigInts)），这尤其有用，因为斐波那契数以指数级速度增长，并会迅速溢出任何固定精度类型，如 `Int`（见 [Overflow behavior](@ref)）。然而，如果我们将函数声明为 `fib(n::Int)`，则会无缘无故地阻止对 `BigInt` 的应用。一般来说，你应该为参数使用最通用的适用抽象类型，**在不确定时，省略参数类型**。如果它们变得必要，你总是可以稍后添加参数类型规范，并且省略它们不会牺牲性能或功能。

## The `return` Keyword

函数返回的值是最后一个被评估的表达式的值，默认情况下，这是函数定义主体中的最后一个表达式。在前一节的示例函数 `f` 中，这就是表达式 `x + y` 的值。作为替代，在许多其他语言中，`return` 关键字使函数立即返回，提供一个返回值的表达式：

```julia
function g(x, y)
    return x * y
    x + y
end
```

由于函数定义可以在交互式会话中输入，因此比较这些定义很容易：

```jldoctest
julia> f(x, y) = x + y
f (generic function with 1 method)

julia> function g(x, y)
           return x * y
           x + y
       end
g (generic function with 1 method)

julia> f(2, 3)
5

julia> g(2, 3)
6
```

当然，在像 `g` 这样的纯线性函数体中，使用 `return` 是没有意义的，因为表达式 `x + y` 从未被评估，我们可以简单地将 `x * y` 作为函数中的最后一个表达式，并省略 `return`。然而，与其他控制流结合时，`return` 是非常有用的。这里，例如，有一个函数计算直角三角形的斜边长度，边长为 `x` 和 `y`，以避免溢出：

```jldoctest
julia> function hypot(x, y)
           x = abs(x)
           y = abs(y)
           if x > y
               r = y/x
               return x*sqrt(1 + r*r)
           end
           if y == 0
               return zero(x)
           end
           r = x/y
           return y*sqrt(1 + r*r)
       end
hypot (generic function with 1 method)

julia> hypot(3, 4)
5.0
```

这个函数有三个可能的返回点，根据 `x` 和 `y` 的值返回三个不同表达式的值。最后一行的 `return` 可以省略，因为它是最后一个表达式。

### [Return type](@id man-functions-return-type)

可以在函数声明中使用 `::` 运算符指定返回类型。这将返回值转换为指定的类型。

```jldoctest
julia> function g(x, y)::Int8
           return x * y
       end;

julia> typeof(g(1, 2))
Int8
```

此函数将始终返回一个 `Int8`，无论 `x` 和 `y` 的类型如何。有关返回类型的更多信息，请参见 [Type Declarations](@ref)。

返回类型声明在 Julia 中是 **很少使用** 的：一般来说，你应该编写“类型稳定”的函数，让 Julia 的编译器能够自动推断返回类型。有关更多信息，请参见 [Performance Tips](@ref man-performance-tips) 章节。

### Returning nothing

对于不需要返回值的函数（仅用于某些副作用的函数），Julia 的约定是返回值 [`nothing`](@ref)：

```julia
function printx(x)
    println("x = $x")
    return nothing
end
```

这是一个*约定*，因为`nothing`不是Julia的关键字，而只是类型为`Nothing`的单例对象。此外，您可能会注意到上面的`printx`函数示例是人为构造的，因为`println`已经返回`nothing`，因此`return`行是多余的。

有两种可能的简化形式用于 `return nothing` 表达式。一方面，`return` 关键字隐式返回 `nothing`，因此可以单独使用。另一方面，由于函数隐式返回其最后一个被评估的表达式，当 `nothing` 是最后一个表达式时，可以单独使用。选择使用 `return nothing` 而不是单独使用 `return` 或 `nothing` 是编码风格的问题。

## Operators Are Functions

在 Julia 中，大多数运算符只是具有特殊语法支持的函数。（例外是具有特殊求值语义的运算符，如 `&&` 和 `||`。这些运算符不能是函数，因为 [Short-Circuit Evaluation](@ref) 要求它们的操作数在运算符求值之前不被求值。）因此，您也可以像使用其他函数一样，使用带括号的参数列表来应用它们：

```jldoctest
julia> 1 + 2 + 3
6

julia> +(1, 2, 3)
6
```

中缀形式与函数应用形式完全等价——实际上，前者在内部被解析为产生函数调用。这也意味着您可以像处理其他函数值一样，分配和传递运算符，例如 [`+`](@ref) 和 [`*`](@ref)：

```jldoctest
julia> f = +;

julia> f(1, 2, 3)
6
```

在名称 `f` 下，该函数不支持中缀表示法。

## Operators With Special Names

一些特殊表达式对应于调用具有不明显名称的函数。这些是：

| Expression            | Calls                                    |
|:--------------------- |:---------------------------------------- |
| `[A B C ...]`         | [`hcat`](@ref)                           |
| `[A; B; C; ...]`      | [`vcat`](@ref)                           |
| `[A B; C D; ...]`     | [`hvcat`](@ref)                          |
| `[A; B;; C; D;; ...]` | [`hvncat`](@ref)                         |
| `A'`                  | [`adjoint`](@ref)                        |
| `A[i]`                | [`getindex`](@ref)                       |
| `A[i] = x`            | [`setindex!`](@ref)                      |
| `A.n`                 | [`getproperty`](@ref Base.getproperty)   |
| `A.n = x`             | [`setproperty!`](@ref Base.setproperty!) |

请注意，类似于 `[A; B;; C; D;; ...]` 的表达式，但有超过两个连续的 `;` 也对应于 `hvncat` 调用。

## [Anonymous Functions](@id man-anonymous-functions)

在 Julia 中，函数是 [first-class objects](https://en.wikipedia.org/wiki/First-class_citizen)：它们可以被赋值给变量，并可以使用从它们被赋值的变量的标准函数调用语法进行调用。它们可以作为参数使用，也可以作为值返回。它们还可以匿名创建，而不需要给定名称，使用以下任一语法：

```jldoctest
julia> x -> x^2 + 2x - 1
#1 (generic function with 1 method)

julia> function (x)
           x^2 + 2x - 1
       end
#3 (generic function with 1 method)
```

每个语句创建一个函数，接受一个参数 `x` 并返回多项式 `x^2 + 2x - 1` 在该值处的值。请注意，结果是一个通用函数，但具有基于连续编号的编译器生成的名称。

匿名函数的主要用途是将它们传递给接受其他函数作为参数的函数。一个经典的例子是 [`map`](@ref)，它对数组的每个值应用一个函数，并返回一个包含结果值的新数组：

```jldoctest
julia> map(round, [1.2, 3.5, 1.7])
3-element Vector{Float64}:
 1.0
 4.0
 2.0
```

如果已经存在一个命名函数来执行转换，可以将其作为第一个参数传递给 [`map`](@ref)，这没问题。然而，通常情况下，并不存在一个现成的命名函数。在这些情况下，匿名函数构造允许轻松创建一个一次性函数对象，而无需命名：

```jldoctest
julia> map(x -> x^2 + 2x - 1, [1, 3, -1])
3-element Vector{Int64}:
  2
 14
 -2
```

一个接受多个参数的匿名函数可以使用语法 `(x,y,z)->2x+y-z` 来编写。

匿名函数的参数类型声明与命名函数相同，例如 `x::Integer->2x`。匿名函数的返回类型无法指定。

一个零参数的匿名函数可以写成 `()->2+2`。没有参数的函数的概念可能看起来很奇怪，但在结果不能（或不应该）预先计算的情况下是有用的。例如，Julia 有一个零参数的 [`time`](@ref) 函数，它返回当前的时间（以秒为单位），因此 `seconds = ()->round(Int, time())` 是一个匿名函数，它返回这个时间四舍五入到最接近的整数，并赋值给变量 `seconds`。每次调用这个匿名函数 `seconds()` 时，当前时间将被计算并返回。

## Tuples

Julia 有一个内置的数据结构，称为 *元组*，与函数参数和返回值密切相关。元组是一个固定长度的容器，可以包含任何值，但不能被修改（它是 *不可变* 的）。元组通过逗号和括号构造，可以通过索引访问：

```jldoctest
julia> (1, 1+1)
(1, 2)

julia> (1,)
(1,)

julia> x = (0.0, "hello", 6*7)
(0.0, "hello", 42)

julia> x[2]
"hello"
```

注意，长度为1的元组必须带有逗号书写，即`(1,)`，因为`(1)`只是一个带括号的值。`()`表示空（长度为0）元组。

## Named Tuples

元组的组件可以选择性地命名，在这种情况下构造一个 *命名元组*：

```jldoctest
julia> x = (a=2, b=1+2)
(a = 2, b = 3)

julia> x[1]
2

julia> x.a
2
```

命名元组的字段可以通过点语法 (`x.a`) 以及常规索引语法 (`x[1]` 或 `x[:a]`) 按名称访问。

## [Destructuring Assignment and Multiple Return Values](@id destructuring-assignment)

一个用逗号分隔的变量列表（可选地用括号包裹）可以出现在赋值的左侧：右侧的值通过迭代并依次赋值给每个变量来*解构*。

```jldoctest
julia> (a, b, c) = 1:3
1:3

julia> b
2
```

右侧的值应该是一个迭代器（参见 [Iteration interface](@ref man-interface-iteration)），其长度至少与左侧变量的数量相同（迭代器的多余元素将被忽略）。

这可以用于通过返回元组或其他可迭代值从函数返回多个值。例如，以下函数返回两个值：

```jldoctest foofunc
julia> function foo(a, b)
           a+b, a*b
       end
foo (generic function with 1 method)
```

如果您在交互式会话中调用它而不将返回值分配到任何地方，您将看到返回的元组：

```jldoctest foofunc
julia> foo(2, 3)
(5, 6)
```

解构赋值将每个值提取到一个变量中：

```jldoctest foofunc
julia> x, y = foo(2, 3)
(5, 6)

julia> x
5

julia> y
6
```

另一个常见的用法是交换变量：

```jldoctest foofunc
julia> y, x = x, y
(5, 6)

julia> x
6

julia> y
5
```

如果只需要迭代器的一个子集元素，常见的约定是将被忽略的元素赋值给一个仅由下划线 `_` 组成的变量（这是一个无效的变量名，见 [Allowed Variable Names](@ref man-allowed-variable-names)）：

```jldoctest
julia> _, _, _, d = 1:10
1:10

julia> d
4
```

其他有效的左侧表达式可以用作赋值列表的元素，这将调用 [`setindex!`](@ref) 或 [`setproperty!`](@ref)，或者递归解构迭代器的单个元素：

```jldoctest
julia> X = zeros(3);

julia> X[1], (a, b) = (1, (2, 3))
(1, (2, 3))

julia> X
3-element Vector{Float64}:
 1.0
 0.0
 0.0

julia> a
2

julia> b
3
```

!!! compat "Julia 1.6"
    `...` 的赋值需要 Julia 1.6


如果赋值列表中的最后一个符号后面加上 `...`（称为 *slurping*），那么它将被赋值为右侧迭代器中剩余元素的集合或惰性迭代器：

```jldoctest
julia> a, b... = "hello"
"hello"

julia> a
'h': ASCII/Unicode U+0068 (category Ll: Letter, lowercase)

julia> b
"ello"

julia> a, b... = Iterators.map(abs2, 1:4)
Base.Generator{UnitRange{Int64}, typeof(abs2)}(abs2, 1:4)

julia> a
1

julia> b
Base.Iterators.Rest{Base.Generator{UnitRange{Int64}, typeof(abs2)}, Int64}(Base.Generator{UnitRange{Int64}, typeof(abs2)}(abs2, 1:4), 1)
```

查看 [`Base.rest`](@ref) 以获取有关特定迭代器的精确处理和自定义的详细信息。

!!! compat "Julia 1.9"
    `...` 在赋值的非最终位置需要 Julia 1.9


在任务中发出啧啧声也可以发生在任何其他位置。然而，与在集合末尾发出啧啧声不同，这种情况总是充满热情的。

```jldoctest
julia> a, b..., c = 1:5
1:5

julia> a
1

julia> b
3-element Vector{Int64}:
 2
 3
 4

julia> c
5

julia> front..., tail = "Hi!"
"Hi!"

julia> front
"Hi"

julia> tail
'!': ASCII/Unicode U+0021 (category Po: Punctuation, other)
```

这是通过函数 [`Base.split_rest`](@ref) 实现的。

请注意，对于可变参数函数定义，吸收（slurping）仍然仅允许在最后一个位置。这不适用于 [single argument destructuring](@ref man-argument-destructuring)，因为这不会影响方法调度：

```jldoctest
julia> f(x..., y) = x
ERROR: syntax: invalid "..." on non-final argument
Stacktrace:
[...]

julia> f((x..., y)) = x
f (generic function with 1 method)

julia> f((1, 2, 3))
(1, 2)
```

## Property destructuring

除了基于迭代的解构外，赋值的右侧也可以使用属性名称进行解构。这遵循命名元组的语法，并通过使用 `getproperty` 将右侧赋值中具有相同名称的属性分配给左侧的每个变量：

```jldoctest
julia> (; b, a) = (a=1, b=2, c=3)
(a = 1, b = 2, c = 3)

julia> a
1

julia> b
2
```

## [Argument destructuring](@id man-argument-destructuring)

解构特性也可以在函数参数中使用。如果函数参数名称写成元组（例如`(x, y)`）而不仅仅是一个符号，那么将为您插入赋值`(x, y) = argument`：

```julia-repl
julia> minmax(x, y) = (y < x) ? (y, x) : (x, y)

julia> gap((min, max)) = max - min

julia> gap(minmax(10, 2))
8
```

注意到在 `gap` 的定义中有额外的一对括号。如果没有这些，`gap` 将是一个两个参数的函数，而这个例子将无法工作。

同样，属性解构也可以用于函数参数：

```julia-repl
julia> foo((; x, y)) = x + y
foo (generic function with 1 method)

julia> foo((x=1, y=2))
3

julia> struct A
           x
           y
       end

julia> foo(A(3, 4))
7
```

对于匿名函数，解构单个参数需要一个额外的逗号：

```
julia> map(((x, y),) -> x + y, [(1, 2), (3, 4)])
2-element Array{Int64,1}:
 3
 7
```

## Varargs Functions

通常，能够编写接受任意数量参数的函数是很方便的。这类函数通常被称为“可变参数”函数，简称“varargs”。您可以通过在最后一个位置参数后面跟一个省略号来定义一个可变参数函数：

```jldoctest barfunc
julia> bar(a, b, x...) = (a, b, x)
bar (generic function with 1 method)
```

变量 `a` 和 `b` 按照惯例绑定到前两个参数值，变量 `x` 绑定到传递给 `bar` 的第一个两个参数之后的零个或多个值的可迭代集合：

```jldoctest barfunc
julia> bar(1, 2)
(1, 2, ())

julia> bar(1, 2, 3)
(1, 2, (3,))

julia> bar(1, 2, 3, 4)
(1, 2, (3, 4))

julia> bar(1, 2, 3, 4, 5, 6)
(1, 2, (3, 4, 5, 6))
```

在所有这些情况下，`x` 被绑定到传递给 `bar` 的尾部值的元组。

可以限制作为可变参数传递的值的数量；这将在 [Parametrically-constrained Varargs methods](@ref) 中讨论。

另一方面，将可迭代集合中的值“展开”为单独的参数传递给函数调用通常是很方便的。为此，在函数调用中也使用 `...`：

```jldoctest barfunc
julia> x = (3, 4)
(3, 4)

julia> bar(1, 2, x...)
(1, 2, (3, 4))
```

在这种情况下，一个值的元组被精确地插入到可变参数调用中，正好在可变参数的位置。然而，这并不一定是这样：

```jldoctest barfunc
julia> x = (2, 3, 4)
(2, 3, 4)

julia> bar(1, x...)
(1, 2, (3, 4))

julia> x = (1, 2, 3, 4)
(1, 2, 3, 4)

julia> bar(x...)
(1, 2, (3, 4))
```

此外，传递给函数调用的可迭代对象不必是元组：

```jldoctest barfunc
julia> x = [3, 4]
2-element Vector{Int64}:
 3
 4

julia> bar(1, 2, x...)
(1, 2, (3, 4))

julia> x = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> bar(x...)
(1, 2, (3, 4))
```

此外，参数被展开到的函数不必是可变参数函数（尽管它通常是）：

```jldoctest
julia> baz(a, b) = a + b;

julia> args = [1, 2]
2-element Vector{Int64}:
 1
 2

julia> baz(args...)
3

julia> args = [1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> baz(args...)
ERROR: MethodError: no method matching baz(::Int64, ::Int64, ::Int64)
The function `baz` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  baz(::Any, ::Any)
   @ Main none:1

Stacktrace:
[...]
```

正如您所看到的，如果在展开的容器中元素的数量不正确，则函数调用将失败，就像如果显式给出了太多参数一样。

## Optional Arguments

通常可以为函数参数提供合理的默认值。这可以节省用户在每次调用时传递每个参数的麻烦。例如，[`Date(y, [m, d])`](@ref) 函数来自 `Dates` 模块，用于构造给定年份 `y`、月份 `m` 和日期 `d` 的 `Date` 类型。然而，`m` 和 `d` 参数是可选的，它们的默认值为 `1`。这种行为可以简洁地表示为：

```jldoctest date_default_args
julia> using Dates

julia> function date(y::Int64, m::Int64=1, d::Int64=1)
           err = Dates.validargs(Date, y, m, d)
           err === nothing || throw(err)
           return Date(Dates.UTD(Dates.totaldays(y, m, d)))
       end
date (generic function with 3 methods)
```

请注意，这一定义调用了 `Date` 函数的另一个方法，该方法接受一个类型为 `UTInstant{Day}` 的参数。

根据这个定义，该函数可以使用一个、两个或三个参数进行调用，当仅指定一个或两个参数时，`1`会自动传递：

```jldoctest date_default_args
julia> date(2000, 12, 12)
2000-12-12

julia> date(2000, 12)
2000-12-01

julia> date(2000)
2000-01-01
```

可选参数实际上只是编写具有不同参数数量的多个方法定义的便捷语法（请参见 [Note on Optional and keyword Arguments](@ref)）。可以通过调用 `methods` 函数来检查我们的 `date` 函数示例：

```julia-repl
julia> methods(date)
# 3 methods for generic function "date":
[1] date(y::Int64) in Main at REPL[1]:1
[2] date(y::Int64, m::Int64) in Main at REPL[1]:1
[3] date(y::Int64, m::Int64, d::Int64) in Main at REPL[1]:1
```

## Keyword Arguments

某些函数需要大量的参数，或者具有大量的行为。记住如何调用这些函数可能会很困难。关键字参数可以通过允许按名称而不是仅按位置识别参数，使这些复杂的接口更易于使用和扩展。

例如，考虑一个绘制线条的函数 `plot`。这个函数可能有许多选项，用于控制线条样式、宽度、颜色等等。如果它接受关键字参数，一个可能的调用方式是 `plot(x, y, width=2)`，在这里我们选择只指定线条宽度。请注意，这有两个目的。调用更易于阅读，因为我们可以用其含义来标记参数。它还使得可以以任意顺序传递大量参数的任何子集。

带有关键字参数的函数在签名中使用分号定义：

```julia
function plot(x, y; style="solid", width=1, color="black")
    ###
end
```

当函数被调用时，分号是可选的：可以调用 `plot(x, y, width=2)` 或 `plot(x, y; width=2)`，但前一种风格更常见。只有在传递可变参数或计算关键字时，如下所述，才需要显式的分号。

关键字参数的默认值仅在必要时（当未传递相应的关键字参数时）进行评估，并且是从左到右的顺序。因此，默认表达式可以引用之前的关键字参数。

关键字参数的类型可以明确如下：

```julia
function f(; x::Int=1)
    ###
end
```

关键字参数也可以在可变参数函数中使用：

```julia
function plot(x...; style="solid")
    ###
end
```

额外的关键字参数可以使用 `...` 收集，就像可变参数函数一样：

```julia
function f(x; y=0, kwargs...)
    ###
end
```

在 `f` 内部，`kwargs` 将是一个不可变的键值迭代器，遍历一个命名元组。命名元组（以及具有 `Symbol` 键的字典，以及其他以符号作为第一个值的两值集合的迭代器）可以通过在调用中使用分号作为关键字参数传递，例如 `f(x, z=1; kwargs...)`。

如果在方法定义中未为关键字参数分配默认值，则该参数是*必需的*：如果调用者未为其分配值，将抛出一个 [`UndefKeywordError`](@ref) 异常：

```julia
function f(x; y)
    ###
end
f(3, y=5) # ok, y is assigned
f(3)      # throws UndefKeywordError(:y)
```

一个人还可以在分号后传递 `key => value` 表达式。例如，`plot(x, y; :width => 2)` 等价于 `plot(x, y, width=2)`。在关键字名称在运行时计算的情况下，这非常有用。

当裸标识符或点表达式出现在分号后时，关键字参数名称由标识符或字段名称隐含。例如 `plot(x, y; width)` 等价于 `plot(x, y; width=width)`，而 `plot(x, y; options.width)` 等价于 `plot(x, y; width=options.width)`。

关键字参数的性质使得可以多次指定相同的参数。例如，在调用 `plot(x, y; options..., width=2)` 时，`options` 结构中也可能包含 `width` 的值。在这种情况下，最右边的出现优先；在这个例子中，`width` 确定为 `2`。然而，显式地多次指定相同的关键字参数，例如 `plot(x, y, width=2, width=3)`，是不允许的，并会导致语法错误。

## Evaluation Scope of Default Values

当可选参数和关键字参数的默认表达式被求值时，只有*之前*的参数在作用域内。例如，给定以下定义：

```julia
function f(x, a=b, b=1)
    ###
end
```

在 `a=b` 中的 `b` 指的是外部作用域中的 `b`，而不是后续参数 `b`。

## Do-Block Syntax for Function Arguments

将函数作为参数传递给其他函数是一种强大的技术，但其语法并不总是方便。当函数参数需要多行时，这种调用尤其难以编写。作为一个例子，考虑在具有多个案例的函数上调用 [`map`](@ref)：

```julia
map(x->begin
           if x < 0 && iseven(x)
               return 0
           elseif x == 0
               return 1
           else
               return x
           end
       end,
    [A, B, C])
```

Julia 提供了一个保留字 `do` 来更清晰地重写这段代码：

```julia
map([A, B, C]) do x
    if x < 0 && iseven(x)
        return 0
    elseif x == 0
        return 1
    else
        return x
    end
end
```

`do x` 语法创建了一个带有参数 `x` 的匿名函数，并将该匿名函数作为第一个参数传递给 "外部" 函数 - 在这个例子中是 [`map`](@ref)。类似地，`do a,b` 将创建一个带有两个参数的匿名函数。请注意，`do (a,b)` 将创建一个带有一个参数的匿名函数，其参数是一个要解构的元组。一个普通的 `do` 将声明后面的内容是一个形式为 `() -> ...` 的匿名函数。

这些参数的初始化取决于“外部”函数；在这里，[`map`](@ref) 将依次将 `x` 设置为 `A`、`B`、`C`，在每次调用匿名函数时，就像在语法 `map(func, [A, B, C])` 中发生的那样。

这种语法使得使用函数有效地扩展语言变得更加容易，因为调用看起来像正常的代码块。有许多可能的用途与 [`map`](@ref) 完全不同，例如管理系统状态。例如，有一个版本的 [`open`](@ref)，它运行代码以确保打开的文件最终被关闭：

```julia
open("outfile", "w") do io
    write(io, data)
end
```

这是通过以下定义实现的：

```julia
function open(f::Function, args...)
    io = open(args...)
    try
        f(io)
    finally
        close(io)
    end
end
```

在这里，[`open`](@ref) 首先打开文件以进行写入，然后将结果输出流传递给您在 `do ... end` 块中定义的匿名函数。在您的函数退出后，`4d61726b646f776e2e436f64652822222c20226f70656e2229_40726566` 将确保流被正确关闭，无论您的函数是正常退出还是抛出异常。（`try/finally` 结构将在 [Control Flow](@ref) 中描述。）

使用 `do` 块语法时，查看文档或实现有助于了解用户函数的参数是如何初始化的。

一个 `do` 块，像任何其他内部函数一样，可以“捕获”来自其封闭作用域的变量。例如，上述 `open...do` 示例中的变量 `data` 是从外部作用域捕获的。捕获的变量可能会带来性能挑战，如在 [performance tips](@ref man-performance-captured) 中讨论的那样。

## Function composition and piping

在Julia中，函数可以通过组合或管道（链式）将它们结合在一起。

函数组合是将函数组合在一起并将结果应用于参数的过程。您使用函数组合运算符（`∘`）来组合函数，因此 `(f ∘ g)(args...; kw...)` 与 `f(g(args...; kw...))` 是相同的。

您可以在 REPL 和适当配置的编辑器中使用 `\circ<tab>` 输入复合运算符。

例如，`sqrt` 和 `+` 函数可以这样组合：

```jldoctest
julia> (sqrt ∘ +)(3, 6)
3.0
```

这首先将数字相加，然后找到结果的平方根。

下面的示例组合了三个函数，并将结果映射到一个字符串数组上：

```jldoctest
julia> map(first ∘ reverse ∘ uppercase, split("you can compose functions like this"))
6-element Vector{Char}:
 'U': ASCII/Unicode U+0055 (category Lu: Letter, uppercase)
 'N': ASCII/Unicode U+004E (category Lu: Letter, uppercase)
 'E': ASCII/Unicode U+0045 (category Lu: Letter, uppercase)
 'S': ASCII/Unicode U+0053 (category Lu: Letter, uppercase)
 'E': ASCII/Unicode U+0045 (category Lu: Letter, uppercase)
 'S': ASCII/Unicode U+0053 (category Lu: Letter, uppercase)
```

函数链式调用（有时称为“管道”或“使用管道”将数据发送到后续函数）是指将一个函数应用于前一个函数的输出：

```jldoctest
julia> 1:10 |> sum |> sqrt
7.416198487095663
```

这里，`sum` 产生的总和被传递给 `sqrt` 函数。等效的组合是：

```jldoctest
julia> (sqrt ∘ sum)(1:10)
7.416198487095663
```

管道操作符也可以与广播一起使用，表示为 `.|>`，以提供链式/管道和点向量化语法（如下所述）的有用组合。

```jldoctest
julia> ["a", "list", "of", "strings"] .|> [uppercase, reverse, titlecase, length]
4-element Vector{Any}:
  "A"
  "tsil"
  "Of"
 7
```

当将管道与匿名函数结合时，如果后续的管道不应被解析为匿名函数的主体，则必须使用括号。比较：

```jldoctest
julia> 1:3 .|> (x -> x^2) |> sum |> sqrt
3.7416573867739413

julia> 1:3 .|> x -> x^2 |> sum |> sqrt
3-element Vector{Float64}:
 1.0
 2.0
 3.0
```

## [Dot Syntax for Vectorizing Functions](@id man-vectorized)

在技术计算语言中，通常会有“向量化”的函数版本，它简单地将给定的函数 `f(x)` 应用到数组 `A` 的每个元素上，从而通过 `f(A)` 生成一个新数组。这种语法对于数据处理非常方便，但在其他语言中，向量化通常也是为了性能：如果循环很慢，函数的“向量化”版本可以调用用低级语言编写的快速库代码。在 Julia 中，向量化函数 *不是* 性能所必需的，实际上，编写自己的循环通常是有益的（参见 [Performance Tips](@ref man-performance-tips)），但它们仍然可以很方便。因此，*任何* Julia 函数 `f` 都可以通过语法 `f.(A)` 元素级地应用于任何数组（或其他集合）。例如，`sin` 可以这样应用于向量 `A` 中的所有元素：

```jldoctest
julia> A = [1.0, 2.0, 3.0]
3-element Vector{Float64}:
 1.0
 2.0
 3.0

julia> sin.(A)
3-element Vector{Float64}:
 0.8414709848078965
 0.9092974268256817
 0.1411200080598672
```

当然，如果你编写一个专门的 `f` 的 "vector" 方法，例如通过 `f(A::AbstractArray) = map(f, A)`，你可以省略点号，这样的效率与 `f.(A)` 一样高。`f.(A)` 语法的优点在于，哪些函数是可向量化的，不必事先由库的作者决定。

更一般地说，`f.(args...)` 实际上等价于 `broadcast(f, args...)`，这允许你对多个数组（甚至是不同形状的数组）或数组和标量的混合进行操作（参见 [Broadcasting](@ref)）。例如，如果你有 `f(x, y) = 3x + 4y`，那么 `f.(pi, A)` 将返回一个新数组，其中包含 `f(pi,a)` 对于 `A` 中的每个 `a`，而 `f.(vector1, vector2)` 将返回一个新向量，其中包含 `f(vector1[i], vector2[i])` 对于每个索引 `i`（如果向量长度不同则抛出异常）。

```jldoctest
julia> f(x, y) = 3x + 4y;

julia> A = [1.0, 2.0, 3.0];

julia> B = [4.0, 5.0, 6.0];

julia> f.(pi, A)
3-element Vector{Float64}:
 13.42477796076938
 17.42477796076938
 21.42477796076938

julia> f.(A, B)
3-element Vector{Float64}:
 19.0
 26.0
 33.0
```

关键字参数不会被广播，而是简单地传递给函数的每次调用。例如，`round.(x, digits=3)` 等价于 `broadcast(x -> round(x, digits=3), x)`。

此外，*嵌套* `f.(args...)` 调用被 *融合* 成一个单一的 `broadcast` 循环。例如，`sin.(cos.(X))` 等价于 `broadcast(x -> sin(cos(x)), X)`，类似于 `[sin(cos(x)) for x in X]`：对 `X` 只有一个循环，并且为结果分配了一个单一的数组。[相比之下，在典型的“向量化”语言中，`sin(cos(X))` 首先会为 `tmp=cos(X)` 分配一个临时数组，然后在一个单独的循环中计算 `sin(tmp)`，分配第二个数组。] 这种循环融合不是可能发生的编译器优化，而是每当遇到嵌套的 `f.(args...)` 调用时的 *语法保证*。从技术上讲，融合在遇到“非点”函数调用时停止；例如，在 `sin.(sort(cos.(X)))` 中，由于中间的 `sort` 函数，`sin` 和 `cos` 循环无法合并。

最后，最大效率通常在向量化操作的输出数组*预分配*时实现，这样重复调用就不会一次又一次地为结果分配新数组（参见 [Pre-allocating outputs](@ref)）。一种方便的语法是 `X .= ...`，这等同于 `broadcast!(identity, X, ...)`，除了上面提到的，`broadcast!` 循环与任何嵌套的“点”调用融合在一起。例如，`X .= sin.(Y)` 等同于 `broadcast!(sin, X, Y)`，在原地用 `sin.(Y)` 覆盖 `X`。如果左侧是一个数组索引表达式，例如 `X[begin+1:end] .= sin.(Y)`，那么它会转换为对 `view` 的 `broadcast!`，例如 `broadcast!(sin, view(X, firstindex(X)+1:lastindex(X)), Y)`，这样左侧就会在原地更新。

由于在表达式中为许多操作和函数调用添加点可能会很繁琐，并导致代码难以阅读，因此提供了宏 [`@.`](@ref @__dot__)，用于将表达式中的 *每个* 函数调用、操作和赋值转换为“点”版本。

```jldoctest
julia> Y = [1.0, 2.0, 3.0, 4.0];

julia> X = similar(Y); # pre-allocate output array

julia> @. X = sin(cos(Y)) # equivalent to X .= sin.(cos.(Y))
4-element Vector{Float64}:
  0.5143952585235492
 -0.4042391538522658
 -0.8360218615377305
 -0.6080830096407656
```

二元（或一元）运算符如 `.+` 采用相同的机制处理：它们等同于 `broadcast` 调用，并与其他嵌套的“点”调用融合。 `X .+= Y` 等同于 `X .= X .+ Y`，并导致一个融合的就地赋值；另见 [dot operators](@ref man-dot-operators)。

您还可以使用 [`|>`](@ref) 将点操作与函数链式调用结合起来，如下例所示：

```jldoctest
julia> 1:5 .|> [x->x^2, inv, x->2*x, -, isodd]
5-element Vector{Real}:
    1
    0.5
    6
   -4
 true
```

所有在融合广播中的函数总是会对结果的每个元素调用。因此 `X .+ σ .* randn.()` 会将一组独立且同分布的随机值的掩码添加到数组 `X` 的每个元素中，而 `X .+ σ .* randn()` 则会将*相同*的随机样本添加到每个元素中。在广播迭代的一个或多个轴上，如果融合计算是常量，则可能可以利用空间-时间权衡，分配中间值以减少计算次数。更多信息请参见 [performance tips](@ref man-performance-unfuse)。

## Further Reading

我们应该在这里提到，这远不是定义函数的完整图景。Julia 具有复杂的类型系统，并允许根据参数类型进行多重分发。这里给出的示例没有对其参数提供任何类型注释，这意味着它们适用于所有类型的参数。类型系统在 [Types](@ref man-types) 中进行了描述，而根据运行时参数类型选择的方法来定义函数在 [Methods](@ref) 中进行了描述。
