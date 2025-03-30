# Metaprogramming

Lisp 在 Julia 语言中最强大的遗产是其元编程支持。与 Lisp 一样，Julia 将其自己的代码表示为语言本身的数据结构。由于代码由可以在语言内部创建和操作的对象表示，因此程序可以转换和生成自己的代码。这允许在没有额外构建步骤的情况下进行复杂的代码生成，并且还允许真正的 Lisp 风格宏在 [abstract syntax trees](https://en.wikipedia.org/wiki/Abstract_syntax_tree) 的层面上操作。相比之下，预处理器“宏”系统，如 C 和 C++ 的系统，在任何实际解析或解释发生之前执行文本操作和替换。由于 Julia 中的所有数据类型和代码都由 Julia 数据结构表示，因此强大的 [reflection](https://en.wikipedia.org/wiki/Reflection_%28computer_programming%29) 功能可用于探索程序及其类型的内部，就像任何其他数据一样。

!!! warning
    元编程是一种强大的工具，但它引入的复杂性可能使代码更难以理解。例如，正确获取作用域规则可能出乎意料地困难。元编程通常应仅在其他方法如 [higher order functions](@ref man-anonymous-functions) 和 [closures](https://en.wikipedia.org/wiki/Closure_(computer_programming)) 无法应用时使用。

    `eval` 和定义新宏通常应作为最后的手段。几乎从来没有好的理由使用 `Meta.parse` 或将任意字符串转换为 Julia 代码。对于操作 Julia 代码，直接使用 `Expr` 数据结构，以避免 Julia 语法解析的复杂性。

    元编程的最佳用法通常在运行时帮助函数中实现大部分功能，努力最小化它们生成的代码量。


## Program representation

每个 Julia 程序的生命开始于一个字符串：

```jldoctest prog
julia> prog = "1 + 1"
"1 + 1"
```

**接下来会发生什么？**

The next step is to [parse](https://en.wikipedia.org/wiki/Parsing#Computer_languages) each string into an object called an expression, represented by the Julia type [`Expr`](@ref):

```jldoctest prog
julia> ex1 = Meta.parse(prog)
:(1 + 1)

julia> typeof(ex1)
Expr
```

`Expr` 对象包含两个部分：

  * 一个 [`Symbol`](@ref) 识别表达式的类型。一个符号是一个 [interned string](https://en.wikipedia.org/wiki/String_interning) 标识符（下面有更多讨论）。

```jldoctest prog
julia> ex1.head
:call
```

  * 表达式参数，可以是符号、其他表达式或字面值：

```jldoctest prog
julia> ex1.args
3-element Vector{Any}:
  :+
 1
 1
```

表达式也可以直接构造在 [prefix notation](https://en.wikipedia.org/wiki/Polish_notation)：

```jldoctest prog
julia> ex2 = Expr(:call, :+, 1, 1)
:(1 + 1)
```

上述构造的两个表达式——通过解析和直接构造——是等价的：

```jldoctest prog
julia> ex1 == ex2
true
```

**这里的关键点是，Julia 代码在内部被表示为一种数据结构，可以从语言本身访问。**

[`dump`](@ref) 函数提供了 `Expr` 对象的缩进和注释显示：

```jldoctest prog
julia> dump(ex2)
Expr
  head: Symbol call
  args: Array{Any}((3,))
    1: Symbol +
    2: Int64 1
    3: Int64 1
```

`Expr` 对象也可以嵌套：

```jldoctest ex3
julia> ex3 = Meta.parse("(4 + 4) / 2")
:((4 + 4) / 2)
```

另一种查看表达式的方法是使用 `Meta.show_sexpr`，它显示给定 `Expr` 的 [S-expression](https://en.wikipedia.org/wiki/S-expression) 形式，这对 Lisp 用户来说可能非常熟悉。以下是一个展示嵌套 `Expr` 显示的示例：

```jldoctest ex3
julia> Meta.show_sexpr(ex3)
(:call, :/, (:call, :+, 4, 4), 2)
```

### Symbols

`:` 字符在 Julia 中有两种语法用途。第一种形式从有效的标识符创建一个 [`Symbol`](@ref)，一个 [interned string](https://en.wikipedia.org/wiki/String_interning)，作为表达式的一个构建块：

```jldoctest
julia> s = :foo
:foo

julia> typeof(s)
Symbol
```

[`Symbol`](@ref) 构造函数可以接受任意数量的参数，并通过将它们的字符串表示连接在一起创建一个新的符号：

```jldoctest
julia> :foo === Symbol("foo")
true

julia> Symbol("1foo") # `:1foo` would not work, as `1foo` is not a valid identifier
Symbol("1foo")

julia> Symbol("func",10)
:func10

julia> Symbol(:var,'_',"sym")
:var_sym
```

在表达式的上下文中，符号用于指示对变量的访问；当表达式被求值时，符号会被替换为绑定到该符号的值，在适当的 [scope](@ref scope-of-variables) 中。

有时在 `:` 的参数周围需要额外的括号，以避免解析时的歧义：

```jldoctest
julia> :(:)
:(:)

julia> :(::)
:(::)
```

## Expressions and evaluation

### Quoting

`:` 字符的第二个语法目的在于创建表达式对象，而无需使用显式的 [`Expr`](@ref) 构造函数。这被称为 *引用*。`:` 字符后跟成对的括号，围绕着一条 Julia 代码的单一语句，生成一个基于封闭代码的 `Expr` 对象。以下是用于引用算术表达式的短格式示例：

```jldoctest
julia> ex = :(a+b*c+1)
:(a + b * c + 1)

julia> typeof(ex)
Expr
```

（要查看此表达式的结构，请尝试 `ex.head` 和 `ex.args`，或使用 [`dump`](@ref)，如上所示，或 [`Meta.@dump`](@ref)）

请注意，可以使用 [`Meta.parse`](@ref) 或直接的 `Expr` 形式构造等效表达式：

```jldoctest
julia>      :(a + b*c + 1)       ==
       Meta.parse("a + b*c + 1") ==
       Expr(:call, :+, :a, Expr(:call, :*, :b, :c), 1)
true
```

解析器提供的表达式通常只有符号、其他表达式和字面值作为它们的参数，而由 Julia 代码构造的表达式可以有任意运行时值作为参数，而不需要字面形式。在这个特定的例子中，`+` 和 `a` 是符号，`*(b,c)` 是一个子表达式，而 `1` 是一个字面 64 位有符号整数。

有第二种语法形式用于多个表达式的引用：用 `quote ... end` 包围的代码块。

```jldoctest
julia> ex = quote
           x = 1
           y = 2
           x + y
       end
quote
    #= none:2 =#
    x = 1
    #= none:3 =#
    y = 2
    #= none:4 =#
    x + y
end

julia> typeof(ex)
Expr
```

### [Interpolation](@id man-expression-interpolation)

直接构造 [`Expr`](@ref) 对象并传入值参数是强大的，但与“正常”的 Julia 语法相比，`Expr` 构造函数可能显得繁琐。作为替代，Julia 允许将字面量或表达式 *插入* 到引用表达式中。插入通过前缀 `$` 来表示。

在这个例子中，变量 `a` 的值被插值：

```jldoctest interp1
julia> a = 1;

julia> ex = :($a + b)
:(1 + b)
```

插入未引用的表达式是不支持的，并会导致编译时错误：

```jldoctest interp1
julia> $a + b
ERROR: syntax: "$" expression outside quote
```

在这个例子中，元组 `(1,2,3)` 被作为一个表达式插入到条件测试中：

```jldoctest interp1
julia> ex = :(a in $:((1,2,3)) )
:(a in (1, 2, 3))
```

使用 `$` 进行表达式插值的设计故意让人联想到 [string interpolation](@ref string-interpolation) 和 [command interpolation](@ref command-interpolation)。表达式插值允许方便、可读的程序化构建复杂的 Julia 表达式。

### Splatting interpolation

注意，`$` 插值语法仅允许将单个表达式插入到封闭表达式中。偶尔，您会有一个表达式数组，并需要将它们全部作为周围表达式的参数。这可以通过语法 `$(xs...)` 来实现。例如，以下代码生成一个函数调用，其中参数的数量是通过程序确定的：

```jldoctest interp1
julia> args = [:x, :y, :z];

julia> :(f(1, $(args...)))
:(f(1, x, y, z))
```

### Nested quote

自然地，引用表达式可以包含其他引用表达式。在这些情况下，理解插值是如何工作的可能有点棘手。考虑这个例子：

```jldoctest interp1
julia> x = :(1 + 2);

julia> e = quote quote $x end end
quote
    #= none:1 =#
    $(Expr(:quote, quote
    #= none:1 =#
    $(Expr(:$, :x))
end))
end
```

注意到结果包含 `$x`，这意味着 `x` 尚未被评估。换句话说，`$` 表达式“属于”内部引用表达式，因此它的参数仅在内部引用表达式被评估时才会被评估：

```jldoctest interp1
julia> eval(e)
quote
    #= none:1 =#
    1 + 2
end
```

然而，外部的 `quote` 表达式能够在内部的引号中插入 `$` 里的值。这是通过多个 `$` 来实现的：

```jldoctest interp1
julia> e = quote quote $$x end end
quote
    #= none:1 =#
    $(Expr(:quote, quote
    #= none:1 =#
    $(Expr(:$, :(1 + 2)))
end))
end
```

注意到 `(1 + 2)` 现在出现在结果中，而不是符号 `x`。评估这个表达式会得到插值 `3`：

```jldoctest interp1
julia> eval(e)
quote
    #= none:1 =#
    3
end
```

这种行为背后的直觉是，`x` 对于每个 `$` 只被评估一次：一个 `$` 的工作方式类似于 `eval(:x)`，给出 `x` 的值，而两个 `$` 则相当于 `eval(eval(:x))`。

### [QuoteNode](@id man-quote-node)

The usual representation of a `quote` form in an AST is an [`Expr`](@ref) with head `:quote`:

```jldoctest interp1
julia> dump(Meta.parse(":(1+2)"))
Expr
  head: Symbol quote
  args: Array{Any}((1,))
    1: Expr
      head: Symbol call
      args: Array{Any}((3,))
        1: Symbol +
        2: Int64 1
        3: Int64 2
```

正如我们所见，这种表达式支持使用 `$` 进行插值。然而，在某些情况下，有必要引用代码 *而不* 执行插值。这种引用尚未有语法，但在内部表示为 `QuoteNode` 类型的对象：

```jldoctest interp1
julia> eval(Meta.quot(Expr(:$, :(1+2))))
3

julia> eval(QuoteNode(Expr(:$, :(1+2))))
:($(Expr(:$, :(1 + 2))))
```

解析器为简单的引用项（如符号）生成 `QuoteNode`：

```jldoctest interp1
julia> dump(Meta.parse(":x"))
QuoteNode
  value: Symbol x
```

`QuoteNode` 也可以用于某些高级元编程任务。

### Evaluating expressions

给定一个表达式对象，可以使用 [`eval`](@ref) 使 Julia 在全局范围内评估（执行）它：

```jldoctest interp1
julia> ex1 = :(1 + 2)
:(1 + 2)

julia> eval(ex1)
3

julia> ex = :(a + b)
:(a + b)

julia> eval(ex)
ERROR: UndefVarError: `b` not defined in `Main`
[...]

julia> a = 1; b = 2;

julia> eval(ex)
3
```

每个 [module](@ref modules) 都有自己的 [`eval`](@ref) 函数，该函数在其全局作用域中评估表达式。传递给 `4d61726b646f776e2e436f64652822222c20226576616c2229_40726566` 的表达式不仅限于返回值 – 它们还可以具有副作用，从而改变封闭模块环境的状态：

```jldoctest
julia> ex = :(x = 1)
:(x = 1)

julia> x
ERROR: UndefVarError: `x` not defined in `Main`

julia> eval(ex)
1

julia> x
1
```

在这里，表达式对象的评估导致一个值被赋给全局变量 `x`。

由于表达式只是可以通过编程构造并评估的 `Expr` 对象，因此可以动态生成任意代码，然后使用 [`eval`](@ref) 运行。以下是一个简单的示例：

```julia-repl
julia> a = 1;

julia> ex = Expr(:call, :+, a, :b)
:(1 + b)

julia> a = 0; b = 2;

julia> eval(ex)
3
```

`a` 的值用于构造表达式 `ex`，该表达式将 `+` 函数应用于值 1 和变量 `b`。请注意 `a` 和 `b` 使用方式之间的重要区别：

  * 在表达式构造时，*变量* `a` 的值被用作表达式中的即时值。因此，当表达式被求值时，`a` 的值不再重要：表达式中的值已经是 `1`，与 `a` 的值无关。
  * 另一方面，*符号* `:b` 在表达式构造中使用，因此此时变量 `b` 的值无关紧要 – `:b` 只是一个符号，变量 `b` 甚至不需要被定义。然而，在表达式求值时，符号 `:b` 的值通过查找变量 `b` 的值来解析。

### Functions on `Expr`essions

As hinted above, one extremely useful feature of Julia is the capability to generate and manipulate Julia code within Julia itself. We have already seen one example of a function returning [`Expr`](@ref) objects: the [`Meta.parse`](@ref) function, which takes a string of Julia code and returns the corresponding `Expr`. A function can also take one or more `Expr` objects as arguments, and return another `Expr`. Here is a simple, motivating example:

```jldoctest
julia> function math_expr(op, op1, op2)
           expr = Expr(:call, op, op1, op2)
           return expr
       end
math_expr (generic function with 1 method)

julia>  ex = math_expr(:+, 1, Expr(:call, :*, 4, 5))
:(1 + 4 * 5)

julia> eval(ex)
21
```

作为另一个例子，这里有一个函数，它将任何数值参数加倍，但不改变表达式：

```jldoctest
julia> function make_expr2(op, opr1, opr2)
           opr1f, opr2f = map(x -> isa(x, Number) ? 2*x : x, (opr1, opr2))
           retexpr = Expr(:call, op, opr1f, opr2f)
           return retexpr
       end
make_expr2 (generic function with 1 method)

julia> make_expr2(:+, 1, 2)
:(2 + 4)

julia> ex = make_expr2(:+, 1, Expr(:call, :*, 5, 8))
:(2 + 5 * 8)

julia> eval(ex)
42
```

## [Macros](@id man-macros)

宏提供了一种将生成的代码包含在程序最终主体中的机制。宏将一组参数映射到返回的 *表达式*，并且生成的表达式会直接编译，而不需要运行时 [`eval`](@ref) 调用。宏参数可以包括表达式、字面值和符号。

### Basics

这是一个极其简单的宏：

```jldoctest sayhello
julia> macro sayhello()
           return :( println("Hello, world!") )
       end
@sayhello (macro with 1 method)
```

宏在Julia的语法中有一个专用字符：`@`（at符号），后面跟着在`macro NAME ... end`块中声明的唯一名称。在这个例子中，编译器将把所有`@sayhello`的实例替换为：

```julia
:( println("Hello, world!") )
```

当在 REPL 中输入 `@sayhello` 时，该表达式会立即执行，因此我们只看到评估结果：

```jldoctest sayhello
julia> @sayhello()
Hello, world!
```

现在，考虑一个稍微复杂一点的宏：

```jldoctest sayhello2
julia> macro sayhello(name)
           return :( println("Hello, ", $name) )
       end
@sayhello (macro with 1 method)
```

这个宏接受一个参数：`name`。当遇到 `@sayhello` 时，引用的表达式会被 *展开*，将参数的值插入到最终表达式中：

```jldoctest sayhello2
julia> @sayhello("human")
Hello, human
```

我们可以使用函数 [`macroexpand`](@ref) 查看引用的返回表达式（**重要提示：** 这是一个非常有用的调试宏的工具）：

```julia-repl sayhello2
julia> ex = macroexpand(Main, :(@sayhello("human")) )
:(Main.println("Hello, ", "human"))

julia> typeof(ex)
Expr
```

我们可以看到 `"human"` 字面量已经被插入到表达式中。

还有一个宏 [`@macroexpand`](@ref)，可能比 `macroexpand` 函数更方便：

```jldoctest sayhello2
julia> @macroexpand @sayhello "human"
:(println("Hello, ", "human"))
```

### Hold up: why macros?

我们在前面的章节中已经看到过一个函数 `f(::Expr...) -> Expr`。实际上，[`macroexpand`](@ref) 也是这样的一个函数。那么，宏存在的原因是什么呢？

宏是必要的，因为它们在代码解析时执行，因此，宏允许程序员在完整程序运行之前生成和包含自定义代码片段。为了说明这个区别，考虑以下示例：

```julia-repl whymacros
julia> macro twostep(arg)
           println("I execute at parse time. The argument is: ", arg)
           return :(println("I execute at runtime. The argument is: ", $arg))
       end
@twostep (macro with 1 method)

julia> ex = macroexpand(Main, :(@twostep :(1, 2, 3)) );
I execute at parse time. The argument is: :((1, 2, 3))
```

第一次调用 [`println`](@ref) 是在调用 [`macroexpand`](@ref) 时执行的。结果表达式仅包含第二个 `println`：

```julia-repl whymacros
julia> typeof(ex)
Expr

julia> ex
:(println("I execute at runtime. The argument is: ", $(Expr(:copyast, :($(QuoteNode(:((1, 2, 3)))))))))

julia> eval(ex)
I execute at runtime. The argument is: (1, 2, 3)
```

### Macro invocation

宏的调用遵循以下一般语法：

```julia
@name expr1 expr2 ...
@name(expr1, expr2, ...)
```

注意宏名称前的 `@` 符号以及第一种形式中参数表达式之间没有逗号的特点，第二种形式中 `@name` 后面没有空格。这两种风格不应混合。例如，以下语法与上述示例不同；它将元组 `(expr1, expr2, ...)` 作为一个参数传递给宏：

```julia
@name (expr1, expr2, ...)
```

一种替代方法是将宏与数组字面量（或推导式）并排放置，而不使用括号。在这种情况下，数组将是传递给宏的唯一表达式。以下语法是等效的（并且与 `@name [a b] * v` 不同）：

```julia
@name[a b] * v
@name([a b]) * v
```

重要的是要强调，宏接收其参数作为表达式、字面量或符号。探索宏参数的一种方法是在宏体内调用 [`show`](@ref) 函数：

```jldoctest
julia> macro showarg(x)
           show(x)
           # ... remainder of macro, returning an expression
       end
@showarg (macro with 1 method)

julia> @showarg(a)
:a

julia> @showarg(1+1)
:(1 + 1)

julia> @showarg(println("Yo!"))
:(println("Yo!"))

julia> @showarg(1)        # Numeric literal
1

julia> @showarg("Yo!")    # String literal
"Yo!"

julia> @showarg("Yo! $("hello")")    # String with interpolation is an Expr rather than a String
:("Yo! $("hello")")
```

除了给定的参数列表，每个宏还会传递额外的参数，名为 `__source__` 和 `__module__`。

参数 `__source__` 提供了关于宏调用中 `@` 符号的解析器位置的信息（以 `LineNumberNode` 对象的形式）。这使得宏能够包含更好的错误诊断信息，并且通常被日志、字符串解析宏和文档等使用，例如，以及实现 [`@__LINE__`](@ref)、[`@__FILE__`](@ref) 和 [`@__DIR__`](@ref) 宏。

位置信息可以通过引用 `__source__.line` 和 `__source__.file` 访问：

```jldoctest
julia> macro __LOCATION__(); return QuoteNode(__source__); end
@__LOCATION__ (macro with 1 method)

julia> dump(
            @__LOCATION__(
       ))
LineNumberNode
  line: Int64 2
  file: Symbol none
```

参数 `__module__` 提供了关于宏调用扩展上下文的信息（以 `Module` 对象的形式）。这使得宏能够查找上下文信息，例如现有的绑定，或者将该值作为额外参数插入到当前模块中进行自我反射的运行时函数调用中。

### Building an advanced macro

这是对Julia的[`@assert`](@ref)宏的简化定义：

```jldoctest building
julia> macro assert(ex)
           return :( $ex ? nothing : throw(AssertionError($(string(ex)))) )
       end
@assert (macro with 1 method)
```

此宏可以这样使用：

```jldoctest building
julia> @assert 1 == 1.0

julia> @assert 1 == 0
ERROR: AssertionError: 1 == 0
```

在书写语法的地方，宏调用在解析时被扩展为其返回结果。这相当于写：

```julia
1 == 1.0 ? nothing : throw(AssertionError("1 == 1.0"))
1 == 0 ? nothing : throw(AssertionError("1 == 0"))
```

也就是说，在第一次调用中，表达式 `:(1 == 1.0)` 被拼接到测试条件插槽中，而 `string(:(1 == 1.0))` 的值被拼接到断言消息插槽中。因此，构造的整个表达式被放置在发生 `@assert` 宏调用的语法树中。然后在执行时，如果测试表达式的结果为真，则返回 [`nothing`](@ref)，而如果测试为假，则会引发错误，指示断言的表达式为假。请注意，这不可能写成一个函数，因为只有条件的 *值* 可用，而在错误消息中显示计算该值的表达式将是不可能的。

The actual definition of `@assert` in Julia Base is more complicated. It allows the user to optionally specify their own error message, instead of just printing the failed expression. Just like in functions with a variable number of arguments ([Varargs Functions](@ref)), this is specified with an ellipses following the last argument:

```jldoctest assert2
julia> macro assert(ex, msgs...)
           msg_body = isempty(msgs) ? ex : msgs[1]
           msg = string(msg_body)
           return :($ex ? nothing : throw(AssertionError($msg)))
       end
@assert (macro with 1 method)
```

现在 `@assert` 有两种操作模式，取决于它接收的参数数量！如果只有一个参数，`msgs` 捕获的表达式元组将为空，它的行为与上面的简单定义相同。但现在如果用户指定第二个参数，它将在消息主体中打印，而不是失败的表达式。您可以使用名为 [`@macroexpand`](@ref) 的宏检查宏扩展的结果：

```julia-repl assert2
julia> @macroexpand @assert a == b
:(if Main.a == Main.b
        Main.nothing
    else
        Main.throw(Main.AssertionError("a == b"))
    end)

julia> @macroexpand @assert a==b "a should equal b!"
:(if Main.a == Main.b
        Main.nothing
    else
        Main.throw(Main.AssertionError("a should equal b!"))
    end)
```

还有另一种情况，实际的 `@assert` 宏处理：如果我们想在打印 "a 应该等于 b" 的同时，打印它们的值呢？人们可能会天真地尝试在自定义消息中使用字符串插值，例如 `@assert a==b "a ($a) should equal b ($b)!"`，但这在上述宏中不会按预期工作。你能看出为什么吗？回想一下 [string interpolation](@ref string-interpolation)，插值字符串被重写为对 [`string`](@ref) 的调用。比较：

```jldoctest
julia> typeof(:("a should equal b"))
String

julia> typeof(:("a ($a) should equal b ($b)!"))
Expr

julia> dump(:("a ($a) should equal b ($b)!"))
Expr
  head: Symbol string
  args: Array{Any}((5,))
    1: String "a ("
    2: Symbol a
    3: String ") should equal b ("
    4: Symbol b
    5: String ")!"
```

所以现在，宏接收到的不是一个简单的字符串 `msg_body`，而是一个完整的表达式，需要进行评估才能按预期显示。这个表达式可以直接作为参数插入到 [`string`](@ref) 调用中；请参见 [`error.jl`](https://github.com/JuliaLang/julia/blob/master/base/error.jl) 以获取完整实现。

`@assert` 宏充分利用了在引用表达式中拼接的特性，以简化宏体内表达式的操作。

### Hygiene

在更复杂的宏中出现的一个问题是 [hygiene](https://en.wikipedia.org/wiki/Hygienic_macro)。简而言之，宏必须确保它们在返回的表达式中引入的变量不会意外与它们扩展到的周围代码中的现有变量冲突。相反，作为参数传递给宏的表达式通常*期望*在周围代码的上下文中进行求值，与现有变量进行交互和修改。另一个问题来自于宏可能在与其定义不同的模块中被调用。在这种情况下，我们需要确保所有全局变量都解析到正确的模块。Julia 相较于具有文本宏扩展的语言（如 C）已经具有一个主要优势，因为它只需要考虑返回的表达式。所有其他变量（例如上面 `@assert` 中的 `msg`）遵循 [normal scoping block behavior](@ref scope-of-variables)。

为了演示这些问题，让我们考虑编写一个 `@time` 宏，该宏将一个表达式作为参数，记录时间，评估表达式，再次记录时间，打印前后时间的差异，然后将表达式的值作为其最终值。该宏可能如下所示：

```julia
macro time(ex)
    return quote
        local t0 = time_ns()
        local val = $ex
        local t1 = time_ns()
        println("elapsed time: ", (t1-t0)/1e9, " seconds")
        val
    end
end
```

在这里，我们希望 `t0`、`t1` 和 `val` 是私有临时变量，并且我们希望 `time_ns` 指的是 Julia Base 中的 [`time_ns`](@ref) 函数，而不是用户可能拥有的任何 `time_ns` 变量（`println` 也是如此）。想象一下，如果用户表达式 `ex` 还包含对名为 `t0` 的变量的赋值，或者定义了自己的 `time_ns` 变量，可能会出现什么问题。我们可能会遇到错误，或者神秘的错误行为。

Julia 的宏扩展器以以下方式解决这些问题。首先，宏结果中的变量被分类为局部或全局。如果一个变量被赋值（且未声明为全局），被声明为局部，或用作函数参数名称，则该变量被视为局部变量。否则，它被视为全局变量。然后，局部变量被重命名为唯一（使用 [`gensym`](@ref) 函数，该函数生成新的符号），全局变量在宏定义环境中被解析。因此，上述两个问题都得到了处理；宏的局部变量不会与任何用户变量冲突，而 `time_ns` 和 `println` 将引用 Julia Base 的定义。

然而，仍然存在一个问题。考虑以下对该宏的使用：

```julia
module MyModule
import Base.@time

time_ns() = ... # compute something

@time time_ns()
end
```

这里用户表达式 `ex` 是对 `time_ns` 的调用，但并不是宏使用的同一个 `time_ns` 函数。它显然指的是 `MyModule.time_ns`。因此，我们必须安排在宏调用环境中解析 `ex` 中的代码。这是通过用 [`esc`](@ref) "转义" 表达式来完成的：

```julia
macro time(ex)
    ...
    local val = $(esc(ex))
    ...
end
```

以这种方式包裹的表达式将被宏扩展器忽略，并原样粘贴到输出中。因此，它将在宏调用环境中被解析。

这种转义机制可以在必要时用于“违反”卫生，以引入或操纵用户变量。例如，以下宏将 `x` 设置为调用环境中的零：

```jldoctest
julia> macro zerox()
           return esc(:(x = 0))
       end
@zerox (macro with 1 method)

julia> function foo()
           x = 1
           @zerox
           return x # is zero
       end
foo (generic function with 1 method)

julia> foo()
0
```

这种变量的操控应该谨慎使用，但有时非常方便。

正确理解卫生规则可能是一个艰巨的挑战。在使用宏之前，您可能想考虑函数闭包是否足够。另一个有用的策略是尽可能将工作推迟到运行时。例如，许多宏只是将它们的参数包装在 `QuoteNode` 或其他类似的 [`Expr`](@ref) 中。这方面的一些例子包括 `@task body`，它简单地返回 `schedule(Task(() -> $body))`，以及 `@eval expr`，它简单地返回 `eval(QuoteNode(expr))`。

为了演示，我们可以将上面的 `@time` 示例重写为：

```julia
macro time(expr)
    return :(timeit(() -> $(esc(expr))))
end
function timeit(f)
    t0 = time_ns()
    val = f()
    t1 = time_ns()
    println("elapsed time: ", (t1-t0)/1e9, " seconds")
    return val
end
```

然而，我们这样做是有充分理由的：将 `expr` 包裹在一个新的作用域块（匿名函数）中也会稍微改变表达式的含义（其中任何变量的作用域），而我们希望 `@time` 的使用对被包裹的代码影响最小。

### Macros and dispatch

宏，就像 Julia 函数一样，是通用的。这意味着它们也可以有多个方法定义，这要归功于多重分发：

```jldoctest macromethods
julia> macro m end
@m (macro with 0 methods)

julia> macro m(args...)
           println("$(length(args)) arguments")
       end
@m (macro with 1 method)

julia> macro m(x,y)
           println("Two arguments")
       end
@m (macro with 2 methods)

julia> @m "asd"
1 arguments

julia> @m 1 2
Two arguments
```

然而，人们应该记住，宏调度是基于传递给宏的AST类型，而不是AST在运行时评估的类型：

```jldoctest macromethods
julia> macro m(::Int)
           println("An Integer")
       end
@m (macro with 3 methods)

julia> @m 2
An Integer

julia> x = 2
2

julia> @m x
1 arguments
```

## Code Generation

当需要大量重复的样板代码时，通常会以编程方式生成它以避免冗余。在大多数语言中，这需要额外的构建步骤，以及一个单独的程序来生成重复的代码。在Julia中，表达式插值和 [`eval`](@ref) 允许这种代码生成在程序执行的正常过程中进行。例如，考虑以下自定义类型

```jldoctest mynumber-codegen
struct MyNumber
    x::Float64
end
# output

```

我们想要为其添加一些方法。我们可以在以下循环中以编程方式做到这一点：

```jldoctest mynumber-codegen
for op = (:sin, :cos, :tan, :log, :exp)
    eval(quote
        Base.$op(a::MyNumber) = MyNumber($op(a.x))
    end)
end
# output

```

我们现在可以使用这些函数与我们的自定义类型：

```jldoctest mynumber-codegen
julia> x = MyNumber(π)
MyNumber(3.141592653589793)

julia> sin(x)
MyNumber(1.2246467991473532e-16)

julia> cos(x)
MyNumber(-1.0)
```

以这种方式，Julia 充当其自身的 [preprocessor](https://en.wikipedia.org/wiki/Preprocessor)，并允许从语言内部生成代码。上述代码可以使用 `:` 前缀引用形式稍微简洁地编写：

```julia
for op = (:sin, :cos, :tan, :log, :exp)
    eval(:(Base.$op(a::MyNumber) = MyNumber($op(a.x))))
end
```

这种语言内代码生成的方式，然而，使用 `eval(quote(...))` 模式是相当常见的，因此 Julia 提供了一个宏来简化这个模式：

```julia
for op = (:sin, :cos, :tan, :log, :exp)
    @eval Base.$op(a::MyNumber) = MyNumber($op(a.x))
end
```

[`@eval`](@ref) 宏将此调用重写为与上述较长版本完全等效。对于较长的生成代码块，传递给 `4d61726b646f64652822222c2022406576616c2229_40726566` 的表达式参数可以是一个块：

```julia
@eval begin
    # multiple lines
end
```

## [Non-Standard String Literals](@id meta-non-standard-string-literals)

回想一下 [Strings](@ref non-standard-string-literals)，以标识符为前缀的字符串字面量称为非标准字符串字面量，并且可以具有与未前缀字符串字面量不同的语义。例如：

  * `r"^\s*(?:#|$)"` 产生了一个 [regular expression object](@ref man-regex-literals) 而不是一个字符串。
  * `b"DATA\xff\u2200"` 是一个 [byte array literal](@ref man-byte-array-literals) 对应于 `[68,65,84,65,255,226,136,128]`。

或许令人惊讶的是，这些行为并不是硬编码在 Julia 解析器或编译器中的。相反，它们是通过一个任何人都可以使用的通用机制提供的自定义行为：带前缀的字符串字面量被解析为对特定命名宏的调用。例如，正则表达式宏就是以下内容：

```julia
macro r_str(p)
    Regex(p)
end
```

这就是全部。这个宏表示字符串字面量 `r"^\s*(?:#|$)"` 的字面内容应该传递给 `@r_str` 宏，并且该扩展的结果应该放置在字符串字面量出现的语法树中。换句话说，表达式 `r"^\s*(?:#|$)"` 等同于将以下对象直接放入语法树中：

```julia
Regex("^\\s*(?:#|\$)")
```

字符串字面量形式不仅更短且更方便，而且效率更高：由于正则表达式在代码编译时被编译，并且 `Regex` 对象实际上是在 *代码编译时* 创建的，因此编译只发生一次，而不是每次代码执行时都发生。考虑正则表达式在循环中出现的情况：

```julia
for line = lines
    m = match(r"^\s*(?:#|$)", line)
    if m === nothing
        # non-comment
    else
        # comment
    end
end
```

由于正则表达式 `r"^\s*(?:#|$)"` 在解析此代码时被编译并插入到语法树中，因此该表达式只会编译一次，而不是每次执行循环时都编译。为了在不使用宏的情况下实现这一点，必须像这样编写这个循环：

```julia
re = Regex("^\\s*(?:#|\$)")
for line = lines
    m = match(re, line)
    if m === nothing
        # non-comment
    else
        # comment
    end
end
```

此外，如果编译器无法确定正则表达式对象在所有循环中都是常量，则某些优化可能无法实现，使得这个版本仍然不如上面的字面形式高效。当然，仍然有一些情况是非字面形式更方便的：如果需要将变量插入到正则表达式中，就必须采取这种更冗长的方法；在正则表达式模式本身是动态的、可能在每次循环迭代时变化的情况下，必须在每次迭代中构造一个新的正则表达式对象。然而，在绝大多数使用情况下，正则表达式并不是基于运行时数据构造的。在这些大多数情况下，将正则表达式写为编译时值的能力是无价的。

用户定义字符串字面量的机制是深刻而强大的。朱莉娅的非标准字面量不仅使用它实现，命令字面量语法（``` `echo "Hello, $person"` ```）也使用以下看似无害的宏实现：

```julia
macro cmd(str)
    :(cmd_gen($(shell_parse(str)[1])))
end
```

当然，这个宏定义中隐藏了大量复杂性，但它们只是函数，完全用Julia编写。你可以阅读它们的源代码，确切地了解它们的功能——它们所做的就是构造表达式对象，以便插入到你程序的语法树中。

像字符串字面量一样，命令字面量也可以通过标识符前缀形成所谓的非标准命令字面量。这些命令字面量被解析为对特殊命名宏的调用。例如，语法 ```custom`literal` ``` 被解析为 `@custom_cmd "literal"`。Julia 本身不包含任何非标准命令字面量，但包可以利用这种语法。除了不同的语法和 `_cmd` 后缀代替 `_str` 后缀外，非标准命令字面量的行为与非标准字符串字面量完全相同。

如果两个模块提供了同名的非标准字符串或命令字面量，可以通过模块名称来限定字符串或命令字面量。例如，如果 `Foo` 和 `Bar` 都提供了非标准字符串字面量 `@x_str`，那么可以写 `Foo.x"literal"` 或 `Bar.x"literal"` 来消除歧义。

另一种定义宏的方法如下：

```julia
macro foo_str(str, flag)
    # do stuff
end
```

此宏可以使用以下语法调用：

```julia
foo"str"flag
```

上述语法中的标志类型将是一个 `String`，其内容为字符串字面量后面的所有内容。

## Generated functions

一个非常特殊的宏是 [`@generated`](@ref)，它允许你定义所谓的 *生成函数*。这些函数能够根据其参数的类型生成专门的代码，具有比多重分发更大的灵活性和/或更少的代码。虽然宏在解析时处理表达式，无法访问其输入的类型，但生成函数在参数类型已知但函数尚未编译时进行扩展。

生成的函数声明返回一个引用的表达式，而不是执行某些计算或操作，该表达式随后形成与参数类型对应的方法的主体。当调用生成的函数时，它返回的表达式会被编译并运行。为了提高效率，结果通常会被缓存。为了使其可推断，仅允许使用语言的有限子集。因此，生成的函数提供了一种灵活的方式，将工作从运行时转移到编译时，但代价是对允许的构造施加了更大的限制。

在定义生成函数时，与普通函数有五个主要区别：

1. 您使用 `@generated` 宏注释函数声明。这向 AST 添加了一些信息，让编译器知道这是一个生成的函数。
2. 在生成的函数体内，您只能访问参数的*类型*，而不能访问它们的值。
3. 而不是计算某些内容或执行某些操作，您返回一个*引用表达式*，该表达式在求值时会执行您想要的操作。
4. 生成的函数仅允许调用在生成函数定义*之前*定义的函数。（未遵循此规则可能会导致出现引用未来世界年龄中函数的`MethodErrors`。）
5. 生成的函数不得*改变*或*观察*任何非常量全局状态（例如，IO、锁、非本地字典，或使用 [`hasmethod`](@ref)）。这意味着它们只能读取全局常量，并且不能有任何副作用。换句话说，它们必须是完全纯粹的。由于实现限制，这也意味着它们目前无法定义闭包或生成器。

最简单的方式是通过一个例子来说明。我们可以声明一个生成的函数 `foo` 为

```jldoctest generated
julia> @generated function foo(x)
           Core.println(x)
           return :(x * x)
       end
foo (generic function with 1 method)
```

注意到主体返回的是一个引用的表达式，即 `:(x * x)`，而不仅仅是 `x * x` 的值。

从调用者的角度来看，这与常规函数是相同的；实际上，您不必知道您是在调用常规函数还是生成的函数。让我们看看 `foo` 的表现：

```jldoctest generated
julia> x = foo(2); # note: output is from println() statement in the body
Int64

julia> x           # now we print x
4

julia> y = foo("bar");
String

julia> y
"barbar"
```

所以，我们看到在生成的函数体中，`x` 是传递参数的 *类型*，而生成函数返回的值是评估我们从定义中返回的引用表达式的结果，现在使用的是 `x` 的 *值*。

如果我们再次使用已经使用过的类型来评估 `foo`，会发生什么？

```jldoctest generated
julia> foo(4)
16
```

注意，[`Int64`](@ref) 没有打印输出。我们可以看到，生成的函数的主体在这里仅执行了一次，针对特定的参数类型，并且结果被缓存。之后，在这个例子中，第一次调用生成的函数返回的表达式被重新用作方法主体。然而，实际的缓存行为是一个实现定义的性能优化，因此过于依赖这种行为是不合法的。

生成的函数被生成的次数*可能*只有一次，但它*可能*也会更频繁地出现，或者看起来根本没有发生。因此，你*永远*不应该编写具有副作用的生成函数——副作用发生的时间和频率是未定义的。（这对于宏也是如此——就像宏一样，在生成的函数中使用 [`eval`](@ref) 是一个信号，表明你正在以错误的方式进行。然而，与宏不同，运行时系统无法正确处理对 `4d61726b646f776e2e436f64652822222c20226576616c2229_40726566` 的调用，因此这是不允许的。）

同样重要的是要观察 `@generated` 函数如何与方法重定义交互。遵循正确的 `@generated` 函数不得观察任何可变状态或导致全局状态的任何变更的原则，我们可以看到以下行为。请注意，生成的函数 *不能* 调用在生成的函数 *定义* 之前未定义的任何方法。

最初 `f(x)` 只有一个定义

```jldoctest redefinition
julia> f(x) = "original definition";
```

定义使用 `f(x)` 的其他操作：

```jldoctest redefinition
julia> g(x) = f(x);

julia> @generated gen1(x) = f(x);

julia> @generated gen2(x) = :(f(x));
```

我们现在为 `f(x)` 添加一些新的定义：

```jldoctest redefinition
julia> f(x::Int) = "definition for Int";

julia> f(x::Type{Int}) = "definition for Type{Int}";
```

并比较这些结果的不同之处：

```jldoctest redefinition
julia> f(1)
"definition for Int"

julia> g(1)
"definition for Int"

julia> gen1(1)
"original definition"

julia> gen2(1)
"definition for Int"
```

每个生成函数的方法都有自己对定义函数的看法：

```jldoctest redefinition
julia> @generated gen1(x::Real) = f(x);

julia> gen1(1)
"definition for Type{Int}"
```

生成的函数 `foo` 的示例上面并没有做任何一个普通函数 `foo(x) = x * x` 无法做到的事情（除了在第一次调用时打印类型，并产生更高的开销）。然而，生成函数的强大之处在于它能够根据传递给它的类型计算不同的引用表达式：

```jldoctest
julia> @generated function bar(x)
           if x <: Integer
               return :(x ^ 2)
           else
               return :(x)
           end
       end
bar (generic function with 1 method)

julia> bar(4)
16

julia> bar("baz")
"baz"
```

（尽管当然这个人为的例子使用多重分发会更容易实现……）

滥用这一点将破坏运行时系统并导致未定义行为：

```jldoctest
julia> @generated function baz(x)
           if rand() < .9
               return :(x^2)
           else
               return :("boo!")
           end
       end
baz (generic function with 1 method)
```

由于生成函数的主体是非确定性的，因此它的行为，以及*所有后续代码的行为*都是未定义的。

*不要复制这些例子！*

这些示例希望能帮助说明生成函数是如何工作的，无论是在定义端还是在调用端；然而，*不要复制它们*，原因如下：

  * `foo` 函数具有副作用（对 `Core.println` 的调用），并且在何时、多少次或多少次发生这些副作用是未定义的。
  * `bar` 函数解决了一个更适合使用多重分发的问题 - 定义 `bar(x) = x` 和 `bar(x::Integer) = x ^ 2` 将实现相同的功能，但它既更简单又更快。
  * `baz` 函数是病态的

请注意，在生成的函数中不应尝试的操作集是无限的，当前运行时系统只能检测到无效操作的一个子集。还有许多其他操作会在没有通知的情况下简单地破坏运行时系统，通常以微妙的方式与错误的定义没有明显的联系。由于函数生成器是在推理过程中运行的，因此必须遵守该代码的所有限制。

一些不应尝试的操作包括：

1. 本地指针的缓存。
2. 以任何方式与 `Core.Compiler` 的内容或方法进行交互。
3. 观察任何可变状态。

      * 对生成的函数的推断可以在*任何*时间运行，包括在您的代码试图观察或改变此状态时。
4. 获取任何锁：您调用的 C 代码可能会内部使用锁（例如，调用 `malloc` 并没有问题，尽管大多数实现内部需要锁），但在执行 Julia 代码时不要尝试持有或获取任何锁。
5. 调用在生成的函数体之后定义的任何函数。对于增量加载的预编译模块，此条件被放宽，以允许调用模块中的任何函数。

好的，现在我们对生成函数的工作原理有了更好的理解，让我们使用它们来构建一些更高级（且有效）的功能...

### An advanced example

Julia的基础库有一个内部的`sub2ind`函数，用于根据一组n个多线性索引计算n维数组的线性索引——换句话说，计算可以用于通过`A[i]`索引数组`A`的索引`i`，而不是`A[x,y,z,...]`。一个可能的实现如下：

```jldoctest sub2ind
julia> function sub2ind_loop(dims::NTuple{N}, I::Integer...) where N
           ind = I[N] - 1
           for i = N-1:-1:1
               ind = I[i]-1 + dims[i]*ind
           end
           return ind + 1
       end;

julia> sub2ind_loop((3, 5), 1, 2)
4
```

可以使用递归来完成相同的事情：

```jldoctest
julia> sub2ind_rec(dims::Tuple{}) = 1;

julia> sub2ind_rec(dims::Tuple{}, i1::Integer, I::Integer...) =
           i1 == 1 ? sub2ind_rec(dims, I...) : throw(BoundsError());

julia> sub2ind_rec(dims::Tuple{Integer, Vararg{Integer}}, i1::Integer) = i1;

julia> sub2ind_rec(dims::Tuple{Integer, Vararg{Integer}}, i1::Integer, I::Integer...) =
           i1 + dims[1] * (sub2ind_rec(Base.tail(dims), I...) - 1);

julia> sub2ind_rec((3, 5), 1, 2)
4
```

这两种实现虽然不同，但本质上做的是相同的事情：在数组的维度上进行运行时循环，将每个维度的偏移量收集到最终索引中。

然而，我们所需的循环信息都嵌入在参数的类型信息中。这使得编译器能够将迭代移到编译时，并完全消除运行时循环。我们可以利用生成的函数来实现类似的效果；在编译器术语中，我们使用生成的函数手动展开循环。主体几乎变得相同，但我们不是计算线性索引，而是构建一个*表达式*来计算索引：

```jldoctest sub2ind_gen
julia> @generated function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

**这将生成什么代码？**

一种简单的方法是将主体提取到另一个（常规）函数中：

```jldoctest sub2ind_gen2
julia> function sub2ind_gen_impl(dims::Type{T}, I...) where T <: NTuple{N,Any} where N
           length(I) == N || return :(error("partial indexing is unsupported"))
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> @generated function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           return sub2ind_gen_impl(dims, I...)
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

我们现在可以执行 `sub2ind_gen_impl` 并检查它返回的表达式：

```jldoctest sub2ind_gen2
julia> sub2ind_gen_impl(Tuple{Int,Int}, Int, Int)
:(((I[1] - 1) + dims[1] * (I[2] - 1)) + 1)
```

所以，这里使用的方法体根本不包含循环 - 只是对两个元组进行索引、乘法和加法/减法。所有的循环都是在编译时执行的，我们在执行过程中完全避免了循环。因此，我们每种类型只循环*一次*，在这种情况下，每个 `N` 只循环一次（除非在边缘情况下函数生成超过一次 - 见上面的免责声明）。

### Optionally-generated functions

生成的函数可以在运行时实现高效率，但伴随着编译时的成本：必须为每种具体参数类型的组合生成一个新的函数体。通常，Julia能够编译适用于任何参数的“通用”版本的函数，但对于生成的函数来说，这是不可能的。这意味着大量使用生成函数的程序可能无法静态编译。

要解决这个问题，语言提供了语法来编写正常的、非生成的生成函数的替代实现。应用于上面的 `sub2ind` 示例，它看起来像这样：

```jldoctest sub2ind_gen_opt
julia> function sub2ind_gen_impl(dims::Type{T}, I...) where T <: NTuple{N,Any} where N
           ex = :(I[$N] - 1)
           for i = (N - 1):-1:1
               ex = :(I[$i] - 1 + dims[$i] * $ex)
           end
           return :($ex + 1)
       end;

julia> function sub2ind_gen_fallback(dims::NTuple{N}, I) where N
           ind = I[N] - 1
           for i = (N - 1):-1:1
               ind = I[i] - 1 + dims[i]*ind
           end
           return ind + 1
       end;

julia> function sub2ind_gen(dims::NTuple{N}, I::Integer...) where N
           length(I) == N || error("partial indexing is unsupported")
           if @generated
               return sub2ind_gen_impl(dims, I...)
           else
               return sub2ind_gen_fallback(dims, I)
           end
       end;

julia> sub2ind_gen((3, 5), 1, 2)
4
```

内部，这段代码创建了该函数的两个实现：一个是生成的实现，其中使用了 `if @generated` 中的第一个块，另一个是正常的实现，其中使用了 `else` 块。在 `if @generated` 块的 `then` 部分，代码具有与其他生成函数相同的语义：参数名称指代类型，代码应返回一个表达式。可能会出现多个 `if @generated` 块，在这种情况下，生成的实现使用所有的 `then` 块，而替代实现使用所有的 `else` 块。

注意，我们在函数的顶部添加了一个错误检查。此代码将在两个版本中通用，并且在两个版本中都是运行时代码（它将被引用并作为表达式从生成的版本返回）。这意味着局部变量的值和类型在代码生成时不可用——代码生成代码只能看到参数的类型。

在这种定义风格中，代码生成特性本质上是一个可选的优化。编译器会在方便时使用它，但否则可能选择使用正常实现。这个风格是首选的，因为它允许编译器做出更多决策，并以更多方式编译程序，并且正常代码比生成代码更易读。然而，使用哪种实现取决于编译器的实现细节，因此两个实现的行为必须完全相同。
