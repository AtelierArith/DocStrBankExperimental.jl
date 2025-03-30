# Control Flow

Julia 提供了多种控制流结构：

  * [Compound Expressions](@ref man-compound-expressions): `开始` 和 `;`。
  * [Conditional Evaluation](@ref man-conditional-evaluation): `如果`-`否则如果`-`否则` 和 `?:`（三元运算符）。
  * [Short-Circuit Evaluation](@ref): 逻辑运算符 `&&` (“与”) 和 `||` (“或”), 以及链式比较。
  * [Repeated Evaluation: Loops](@ref man-loops): `當` 和 `為`.
  * [Exception Handling](@ref): `尝试`-`捕获`, [`error`](@ref) 和 [`throw`](@ref).
  * [Tasks (aka Coroutines)](@ref man-tasks): [`yieldto`](@ref).

前五种控制流机制是高级编程语言的标准。[`Task`](@ref) 并不是那么标准：它们提供了非局部控制流，使得在暂时挂起的计算之间切换成为可能。这是一个强大的构造：异常处理和协作多任务都在 Julia 中使用任务实现。日常编程不需要直接使用任务，但某些问题通过使用任务可以更容易地解决。

## [Compound Expressions](@id man-compound-expressions)

有时，拥有一个单一的表达式来顺序评估多个子表达式是很方便的，它返回最后一个子表达式的值。Julia 中有两种构造可以实现这一点：`begin` 块和 `;` 链。两个复合表达式构造的值都是最后一个子表达式的值。以下是一个 `begin` 块的示例：

```jldoctest
julia> z = begin
           x = 1
           y = 2
           x + y
       end
3
```

由于这些表达式相对较小且简单，它们可以很容易地放在一行上，这就是 `;` 链接语法派上用场的地方：

```jldoctest
julia> z = (x = 1; y = 2; x + y)
3
```

这种语法在 [Functions](@ref man-functions) 中引入的简洁单行函数定义形式中特别有用。尽管这是典型的用法，但并没有要求 `begin` 块必须是多行的，或者 `;` 链接必须是单行的：

```jldoctest
julia> begin x = 1; y = 2; x + y end
3

julia> (x = 1;
        y = 2;
        x + y)
3
```

## [Conditional Evaluation](@id man-conditional-evaluation)

条件评估允许根据布尔表达式的值来评估或不评估代码的某些部分。以下是 `if`-`elseif`-`else` 条件语法的结构：

```julia
if x < y
    println("x is less than y")
elseif x > y
    println("x is greater than y")
else
    println("x is equal to y")
end
```

如果条件表达式 `x < y` 为 `true`，则相应的代码块会被执行；否则，条件表达式 `x > y` 会被评估，如果它为 `true`，则相应的代码块会被执行；如果两个表达式都不为真，则执行 `else` 块。这里是它的实际应用：

```jldoctest
julia> function test(x, y)
           if x < y
               println("x is less than y")
           elseif x > y
               println("x is greater than y")
           else
               println("x is equal to y")
           end
       end
test (generic function with 1 method)

julia> test(1, 2)
x is less than y

julia> test(2, 1)
x is greater than y

julia> test(1, 1)
x is equal to y
```

`elseif` 和 `else` 块是可选的，可以使用任意数量的 `elseif` 块。`if`-`elseif`-`else` 结构中的条件表达式会被评估，直到第一个评估为 `true` 的表达式为止，此后将评估相关的块，并且不再评估其他条件表达式或块。

`if` 块是“泄漏”的，即它们不会引入局部作用域。这意味着在 `if` 子句中定义的新变量可以在 `if` 块之后使用，即使它们之前没有定义。因此，我们可以将上面的 `test` 函数定义为

```jldoctest
julia> function test(x,y)
           if x < y
               relation = "less than"
           elseif x == y
               relation = "equal to"
           else
               relation = "greater than"
           end
           println("x is ", relation, " y.")
       end
test (generic function with 1 method)

julia> test(2, 1)
x is greater than y.
```

变量 `relation` 在 `if` 块内声明，但在外部使用。然而，当依赖于这种行为时，请确保所有可能的代码路径都为该变量定义一个值。对上述函数的以下更改会导致运行时错误。

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function test(x,y)
           if x < y
               relation = "less than"
           elseif x == y
               relation = "equal to"
           end
           println("x is ", relation, " y.")
       end
test (generic function with 1 method)

julia> test(1,2)
x is less than y.

julia> test(2,1)
ERROR: UndefVarError: `relation` not defined in local scope
Stacktrace:
 [1] test(::Int64, ::Int64) at ./none:7
```

`if` 块也会返回一个值，这对来自许多其他语言的用户来说可能显得不太直观。这个值就是在所选择的分支中最后执行语句的返回值，因此

```jldoctest
julia> x = 3
3

julia> if x > 0
           "positive!"
       else
           "negative..."
       end
"positive!"
```

请注意，非常简短的条件语句（单行语句）在Julia中通常使用短路求值来表达，如下一节所述。

与 C、MATLAB、Perl、Python 和 Ruby 不同——但与 Java 以及其他一些更严格的类型语言相似——如果条件表达式的值不是 `true` 或 `false`，则会出现错误：

```jldoctest
julia> if 1
           println("true")
       end
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

此错误表明条件的类型错误：[`Int64`](@ref) 而不是所需的 [`Bool`](@ref)。

所谓的“三元运算符”，`?:`，与`if`-`elseif`-`else`语法密切相关，但用于需要在单个表达式值之间进行条件选择的地方，而不是条件执行较长的代码块。它之所以得名，是因为在大多数语言中，它是唯一一个接受三个操作数的运算符：

```julia
a ? b : c
```

表达式 `a` 在 `?` 之前，是一个条件表达式，三元操作符在条件 `a` 为 `true` 时会计算 `?` 之前的表达式 `b`，而在条件为 `false` 时会计算 `:` 之后的表达式 `c`。请注意，`?` 和 `:` 周围的空格是必需的：像 `a?b:c` 这样的表达式不是有效的三元表达式（但在 `?` 和 `:` 之后换行是可以接受的）。

理解这种行为最简单的方法是查看一个例子。在前面的例子中，`println` 调用被所有三个分支共享：唯一真正的选择是打印哪个字面字符串。这可以使用三元运算符更简洁地编写。为了清晰起见，我们先尝试一个双向版本：

```jldoctest
julia> x = 1; y = 2;

julia> println(x < y ? "less than" : "not less than")
less than

julia> x = 1; y = 0;

julia> println(x < y ? "less than" : "not less than")
not less than
```

如果表达式 `x < y` 为真，则整个三元运算符表达式的值为字符串 `"less than"`，否则其值为字符串 `"not less than"`。原始的三元运算符示例需要将多个三元运算符的使用串联在一起：

```jldoctest
julia> test(x, y) = println(x < y ? "x is less than y"    :
                            x > y ? "x is greater than y" : "x is equal to y")
test (generic function with 1 method)

julia> test(1, 2)
x is less than y

julia> test(2, 1)
x is greater than y

julia> test(1, 1)
x is equal to y
```

为了方便链式调用，运算符从右到左结合。

重要的是，像 `if`-`elseif`-`else` 一样，只有在条件表达式评估为 `true` 或 `false` 时，`:` 前后的表达式才会被评估：

```jldoctest
julia> v(x) = (println(x); x)
v (generic function with 1 method)

julia> 1 < 2 ? v("yes") : v("no")
yes
"yes"

julia> 1 > 2 ? v("yes") : v("no")
no
"no"
```

## Short-Circuit Evaluation

`&&` 和 `||` 运算符在 Julia 中分别对应逻辑“与”和“或”操作，通常用于此目的。然而，它们还有一个额外的特性，即 *短路* 评估：它们不一定会评估第二个参数，如下所述。（还有位运算符 `&` 和 `|` 可以用作逻辑“与”和“或” *而不* 具有短路行为，但请注意，`&` 和 `|` 的优先级高于 `&&` 和 `||`，影响评估顺序。）

短路求值与条件求值非常相似。这种行为在大多数具有 `&&` 和 `||` 布尔运算符的命令式编程语言中都能找到：在一系列通过这些运算符连接的布尔表达式中，仅评估确定整个链的最终布尔值所需的最少数量的表达式。一些语言（如 Python）将它们称为 `and`（`&&`）和 `or`（`||`）。明确来说，这意味着：

  * 在表达式 `a && b` 中，子表达式 `b` 仅在 `a` 的值为 `true` 时才会被求值。
  * 在表达式 `a || b` 中，子表达式 `b` 仅在 `a` 的值为 `false` 时才会被求值。

推理是，如果 `a` 为 `false`，则 `a && b` 必须为 `false`，无论 `b` 的值如何；同样，如果 `a` 为 `true`，则 `a || b` 的值必须为 `true`，无论 `b` 的值如何。`&&` 和 `||` 都是右结合的，但 `&&` 的优先级高于 `||`。很容易对这种行为进行实验：

```jldoctest tandf
julia> t(x) = (println(x); true)
t (generic function with 1 method)

julia> f(x) = (println(x); false)
f (generic function with 1 method)

julia> t(1) && t(2)
1
2
true

julia> t(1) && f(2)
1
2
false

julia> f(1) && t(2)
1
false

julia> f(1) && f(2)
1
false

julia> t(1) || t(2)
1
true

julia> t(1) || f(2)
1
true

julia> f(1) || t(2)
1
2
true

julia> f(1) || f(2)
1
2
false
```

您可以以相同的方式轻松实验各种组合的 `&&` 和 `||` 运算符的结合性和优先级。

这种行为在 Julia 中经常被用来形成非常简短的 `if` 语句的替代品。可以用 `<cond> && <statement>` 来代替 `if <cond> <statement> end`（可以理解为：<cond> *然后* <statement>）。类似地，可以用 `<cond> || <statement>` 来代替 `if ! <cond> <statement> end`（可以理解为：<cond> *或者* <statement>）。

例如，一个递归的阶乘例程可以这样定义：

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function fact(n::Int)
           n >= 0 || error("n must be non-negative")
           n == 0 && return 1
           n * fact(n-1)
       end
fact (generic function with 1 method)

julia> fact(5)
120

julia> fact(0)
1

julia> fact(-1)
ERROR: n must be non-negative
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fact(::Int64) at ./none:2
 [3] top-level scope
```

布尔运算 *不* 使用短路求值可以通过在 [Mathematical Operations and Elementary Functions](@ref) 中引入的按位布尔运算符 `&` 和 `|` 来完成。这些是普通函数，恰好支持中缀运算符语法，但始终会评估它们的参数：

```jldoctest tandf
julia> f(1) & t(2)
1
2
false

julia> t(1) | t(2)
1
2
true
```

就像在 `if`、`elseif` 或三元运算符中使用的条件表达式一样，`&&` 或 `||` 的操作数必须是布尔值（`true` 或 `false`）。在条件链中，除了最后一个条目之外，使用非布尔值是一个错误：

```jldoctest
julia> 1 && true
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

另一方面，任何类型的表达式都可以在条件链的末尾使用。它将根据前面的条件进行评估并返回：

```jldoctest
julia> true && (x = (1, 2, 3))
(1, 2, 3)

julia> false && (x = (1, 2, 3))
false
```

## [Repeated Evaluation: Loops](@id man-loops)

有两种用于重复评估表达式的结构：`while` 循环和 `for` 循环。以下是一个 `while` 循环的示例：

```jldoctest
julia> i = 1;

julia> while i <= 3
           println(i)
           global i += 1
       end
1
2
3
```

`while` 循环评估条件表达式（在这种情况下为 `i <= 3`），只要它保持为 `true`，就会继续评估 `while` 循环的主体。如果在第一次到达 `while` 循环时条件表达式为 `false`，则主体将永远不会被评估。

`for` 循环使得常见的重复评估习惯更容易编写。由于像上面的 `while` 循环那样的计数是如此常见，它可以用 `for` 循环更简洁地表达：

```jldoctest
julia> for i = 1:3
           println(i)
       end
1
2
3
```

这里的 `1:3` 是一个 [`range`](@ref) 对象，表示数字序列 1、2、3。`for` 循环遍历这些值，将每个值依次赋给变量 `i`。一般来说，`for` 结构可以遍历任何“可迭代”对象（或“容器”），从像 `1:3` 或 `1:3:13` 的范围（一个 [`StepRange`](@ref)，表示每隔 3 个整数 1、4、7、…、13）到更通用的容器，如数组，包括 [iterators defined by user code](@ref man-interface-iteration) 或外部包。对于范围以外的容器，通常使用替代（但完全等效的）关键字 `in` 或 `∈`，而不是 `=`，因为这使得代码更清晰易读：

```jldoctest
julia> for i in [1,4,0]
           println(i)
       end
1
4
0

julia> for s ∈ ["foo","bar","baz"]
           println(s)
       end
foo
bar
baz
```

手册的后续部分将介绍和讨论各种类型的可迭代容器（参见，例如，[Multi-dimensional Arrays](@ref man-multi-dim-arrays)）。

一个相当重要的区别在于之前的 `while` 循环形式和 `for` 循环形式之间的作用域。在 `for` 循环中，无论在外部作用域中是否存在同名变量，它总是会在其主体中引入一个新的迭代变量。这意味着，一方面 `i` 不需要在循环之前声明。另一方面，它在循环外不可见，也不会影响外部同名变量。您需要一个新的交互式会话实例或不同的变量名来测试这一点：

```jldoctest
julia> for j = 1:3
           println(j)
       end
1
2
3

julia> j
ERROR: UndefVarError: `j` not defined in `Main`
```

```jldoctest
julia> j = 0;

julia> for j = 1:3
           println(j)
       end
1
2
3

julia> j
0
```

使用 `for outer` 来修改后者的行为并重用现有的局部变量。

查看 [Scope of Variables](@ref scope-of-variables) 以获取有关变量作用域的详细解释，[`outer`](@ref)，以及它在 Julia 中的工作原理。

有时在测试条件未被否定之前终止 `while` 循环的重复，或在达到可迭代对象的末尾之前停止 `for` 循环的迭代是很方便的。这可以通过 `break` 关键字来实现：

```jldoctest
julia> i = 1;

julia> while true
           println(i)
           if i >= 3
               break
           end
           global i += 1
       end
1
2
3

julia> for j = 1:1000
           println(j)
           if j >= 3
               break
           end
       end
1
2
3
```

没有 `break` 关键字，上面的 `while` 循环将永远不会自行终止，而 `for` 循环将迭代到 1000。这两个循环都是通过使用 `break` 提前退出的。

在其他情况下，能够停止一个迭代并立即进入下一个迭代是很方便的。`continue` 关键字可以实现这一点：

```jldoctest
julia> for i = 1:10
           if i % 3 != 0
               continue
           end
           println(i)
       end
3
6
9
```

这是一个有些牵强的例子，因为我们可以通过否定条件并将 `println` 调用放在 `if` 块内来更清晰地产生相同的行为。在实际使用中，`continue` 之后还有更多代码需要评估，并且通常有多个点可以调用 `continue`。

多个嵌套的 `for` 循环可以合并为一个外部循环，从而形成其可迭代对象的笛卡尔积：

```jldoctest
julia> for i = 1:2, j = 3:4
           println((i, j))
       end
(1, 3)
(1, 4)
(2, 3)
(2, 4)
```

使用这种语法，迭代器仍然可以引用外部循环变量；例如，`for i = 1:n, j = 1:i` 是有效的。然而，在这样的循环内部的 `break` 语句会退出整个循环嵌套，而不仅仅是内部循环。每次内部循环运行时，两个变量（`i` 和 `j`）都被设置为它们当前的迭代值。因此，对 `i` 的赋值在后续迭代中将不可见：

```jldoctest
julia> for i = 1:2, j = 3:4
           println((i, j))
           i = 0
       end
(1, 3)
(1, 4)
(2, 3)
(2, 4)
```

如果这个例子被重写为对每个变量使用 `for` 关键字，那么输出将会不同：第二个和第四个值将包含 `0`。

多个容器可以在单个 `for` 循环中同时迭代，使用 [`zip`](@ref)：

```jldoctest
julia> for (j, k) in zip([1 2 3], [4 5 6 7])
           println((j,k))
       end
(1, 4)
(2, 5)
(3, 6)
```

使用 [`zip`](@ref) 将创建一个迭代器，该迭代器是一个元组，包含传递给它的容器的子迭代器。`zip` 迭代器将按顺序遍历所有子迭代器，在 `for` 循环的第 $i$ 次迭代中选择每个子迭代器的第 $i$ 个元素。一旦任何子迭代器耗尽，`for` 循环将停止。

## Exception Handling

当发生意外情况时，函数可能无法向其调用者返回合理的值。在这种情况下，最好让异常情况终止程序并打印诊断错误消息，或者如果程序员提供了处理此类异常情况的代码，则允许该代码采取适当的行动。

### Built-in `Exception`s

`Exception` 在发生意外情况时被抛出。下面列出的内置 `Exception` 都会中断正常的控制流程。

| `Exception`                   |
|:----------------------------- |
| [`ArgumentError`](@ref)       |
| [`BoundsError`](@ref)         |
| [`CompositeException`](@ref)  |
| [`DimensionMismatch`](@ref)   |
| [`DivideError`](@ref)         |
| [`DomainError`](@ref)         |
| [`EOFError`](@ref)            |
| [`ErrorException`](@ref)      |
| [`InexactError`](@ref)        |
| [`InitError`](@ref)           |
| [`InterruptException`](@ref)  |
| `InvalidStateException`       |
| [`KeyError`](@ref)            |
| [`LoadError`](@ref)           |
| [`OutOfMemoryError`](@ref)    |
| [`ReadOnlyMemoryError`](@ref) |
| [`RemoteException`](@ref)     |
| [`MethodError`](@ref)         |
| [`OverflowError`](@ref)       |
| [`Meta.ParseError`](@ref)     |
| [`SystemError`](@ref)         |
| [`TypeError`](@ref)           |
| [`UndefRefError`](@ref)       |
| [`UndefVarError`](@ref)       |
| [`StringIndexError`](@ref)    |

例如，[`sqrt`](@ref) 函数在应用于负实值时会抛出 [`DomainError`](@ref)：

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

您可以通过以下方式定义自己的异常：

```jldoctest
julia> struct MyCustomException <: Exception end
```

### The [`throw`](@ref) function

异常可以通过 [`throw`](@ref) 显式创建。例如，仅对非负数定义的函数可以写成 `4d61726b646f776e2e436f64652822222c20227468726f772229_40726566` 一个 [`DomainError`](@ref) 如果参数为负：

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> f(x) = x>=0 ? exp(-x) : throw(DomainError(x, "argument must be non-negative"))
f (generic function with 1 method)

julia> f(1)
0.36787944117144233

julia> f(-1)
ERROR: DomainError with -1:
argument must be non-negative
Stacktrace:
 [1] f(::Int64) at ./none:1
```

请注意，[`DomainError`](@ref)（不带括号）不是一个例外，而是一种异常。需要调用它以获取一个 `Exception` 对象：

```jldoctest
julia> typeof(DomainError(nothing)) <: Exception
true

julia> typeof(DomainError) <: Exception
false
```

此外，一些异常类型接受一个或多个用于错误报告的参数：

```jldoctest
julia> throw(UndefVarError(:x))
ERROR: UndefVarError: `x` not defined
```

此机制可以通过自定义异常类型轻松实现，遵循 [`UndefVarError`](@ref) 的写法：

```jldoctest
julia> struct MyUndefVarError <: Exception
           var::Symbol
       end

julia> Base.showerror(io::IO, e::MyUndefVarError) = print(io, e.var, " not defined")
```

!!! note
    在编写错误消息时，首个单词首选小写。例如，

    `size(A) == size(B) || throw(DimensionMismatch("A的大小不等于B的大小"))`

    更受欢迎的是

    `size(A) == size(B) || throw(DimensionMismatch("A的大小不等于B的大小"))`

    然而，有时保留首字母大写是有意义的，例如当函数的参数是一个大写字母时：

    `size(A,1) == size(B,2) || throw(DimensionMismatch("A的第一维度..."))`


### Errors

[`error`](@ref) 函数用于生成一个 [`ErrorException`](@ref)，该函数会中断正常的控制流。

假设我们想要立即停止执行，如果取负数的平方根。为此，我们可以定义一个模糊版本的 [`sqrt`](@ref) 函数，如果其参数为负，则引发错误：

```jldoctest fussy_sqrt; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> fussy_sqrt(x) = x >= 0 ? sqrt(x) : error("negative x not allowed")
fussy_sqrt (generic function with 1 method)

julia> fussy_sqrt(2)
1.4142135623730951

julia> fussy_sqrt(-1)
ERROR: negative x not allowed
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fussy_sqrt(::Int64) at ./none:1
 [3] top-level scope
```

如果 `fussy_sqrt` 被另一个函数以负值调用，它不会尝试继续执行调用函数，而是立即返回，在交互式会话中显示错误信息：

```jldoctest fussy_sqrt; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function verbose_fussy_sqrt(x)
           println("before fussy_sqrt")
           r = fussy_sqrt(x)
           println("after fussy_sqrt")
           return r
       end
verbose_fussy_sqrt (generic function with 1 method)

julia> verbose_fussy_sqrt(2)
before fussy_sqrt
after fussy_sqrt
1.4142135623730951

julia> verbose_fussy_sqrt(-1)
before fussy_sqrt
ERROR: negative x not allowed
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fussy_sqrt at ./none:1 [inlined]
 [3] verbose_fussy_sqrt(::Int64) at ./none:3
 [4] top-level scope
```

### The `try/catch` statement

`try/catch` 语句允许测试 `Exception`，并优雅地处理可能会破坏应用程序的情况。例如，在下面的代码中，平方根的函数通常会抛出一个异常。通过在其周围放置一个 `try/catch` 块，我们可以在这里减轻这个问题。您可以选择如何处理这个异常，无论是记录它、返回一个占位符值，还是像下面的例子中那样仅仅打印出一条语句。在决定如何处理意外情况时，需要考虑的一件事是，使用 `try/catch` 块的速度远低于使用条件分支来处理这些情况。下面还有更多使用 `try/catch` 块处理异常的示例：

```jldoctest
julia> try
           sqrt("ten")
       catch e
           println("You should have entered a numeric value")
       end
You should have entered a numeric value
```

`try/catch` 语句还允许将 `Exception` 保存到变量中。以下这个人为的例子计算 `x` 的第二个元素的平方根，如果 `x` 是可索引的， 否则假设 `x` 是一个实数并返回它的平方根：

```jldoctest
julia> sqrt_second(x) = try
           sqrt(x[2])
       catch y
           if isa(y, DomainError)
               sqrt(complex(x[2], 0))
           elseif isa(y, BoundsError)
               sqrt(x)
           end
       end
sqrt_second (generic function with 1 method)

julia> sqrt_second([1 4])
2.0

julia> sqrt_second([1 -4])
0.0 + 2.0im

julia> sqrt_second(9)
3.0

julia> sqrt_second(-9)
ERROR: DomainError with -9.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

请注意，`catch` 后面的符号将始终被解释为异常的名称，因此在编写单行的 `try/catch` 表达式时需要小心。以下代码在发生错误时将 *不* 能返回 `x` 的值：

```julia
try bad() catch x end
```

相反，在 `catch` 后使用分号或插入换行：

```julia
try bad() catch; x end

try bad()
catch
    x
end
```

`try/catch` 结构的强大之处在于能够立即将深度嵌套的计算展开到调用函数栈的更高层次。有些情况下并没有发生错误，但展开栈并将值传递到更高层次的能力是可取的。Julia 提供了 [`rethrow`](@ref)、[`backtrace`](@ref)、[`catch_backtrace`](@ref) 和 [`current_exceptions`](@ref) 函数以实现更高级的错误处理。

### `else` Clauses

!!! compat "Julia 1.8"
    此功能至少需要 Julia 1.8。


在某些情况下，可能不仅希望适当地处理错误情况，还希望仅在 `try` 块成功时运行一些代码。为此，可以在 `catch` 块之后指定一个 `else` 子句，该子句在之前没有抛出错误时运行。与将此代码包含在 `try` 块中的优势在于，任何进一步的错误不会被 `catch` 子句静默捕获。

```julia
local x
try
    x = read("file", String)
catch
    # handle read errors
else
    # do something with x
end
```

!!! note
    `try`、`catch`、`else` 和 `finally` 子句各自引入自己的作用域块，因此如果一个变量仅在 `try` 块中定义，则无法在 `else` 或 `finally` 子句中访问该变量：

    ```jldoctest
    julia> try
               foo = 1
           catch
           else
               foo
           end
    ERROR: UndefVarError: `foo` not defined in `Main`
    Suggestion: check for spelling errors or missing imports.
    ```

    使用 [`local` keyword](@ref local-scope) 在 `try` 块外部，使变量在外部作用域内的任何地方都可访问。


### `finally` Clauses

在执行状态更改或使用文件等资源的代码中，通常需要在代码完成时进行清理工作（例如关闭文件）。异常可能会使这项任务变得复杂，因为它们可能导致代码块在达到正常结束之前退出。`finally`关键字提供了一种在给定代码块退出时运行某些代码的方法，无论它是如何退出的。

例如，以下是我们如何确保打开的文件被关闭：

```julia
f = open("file")
try
    # operate on file f
finally
    close(f)
end
```

当控制离开 `try` 块时（例如由于 `return`，或正常结束），`close(f)` 将被执行。如果 `try` 块由于异常而退出，异常将继续传播。`catch` 块可以与 `try` 和 `finally` 结合使用。在这种情况下，`finally` 块将在 `catch` 处理完错误后运行。

## [Tasks (aka Coroutines)](@id man-tasks)

任务是一种控制流特性，允许以灵活的方式暂停和恢复计算。我们在这里提到它们只是为了完整性；有关详细讨论，请参见 [Asynchronous Programming](@ref man-asynchronous)。
