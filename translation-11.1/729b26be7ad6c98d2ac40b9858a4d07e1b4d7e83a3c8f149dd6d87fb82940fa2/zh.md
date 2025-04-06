# [Scope of Variables](@id scope-of-variables)

变量的 *作用域* 是指变量可访问的代码区域。变量作用域有助于避免变量命名冲突。这个概念是直观的：两个函数都可以有名为 `x` 的参数，而这两个 `x` 并不指代同一事物。同样，还有许多其他情况，不同的代码块可以使用相同的名称而不指代同一事物。相同变量名称是否指代同一事物的规则称为作用域规则；本节将详细说明这些规则。

某些语言构造引入了 *作用域块*，这是一些代码区域，符合某组变量的作用域。变量的作用域不能是任意的源代码行集合；相反，它总是与这些块之一对齐。在 Julia 中有两种主要的作用域，*全局作用域* 和 *局部作用域*。后者可以嵌套。Julia 中还区分了引入“硬作用域”的构造和仅引入“软作用域”的构造，这影响了是否允许 [shadowing](https://en.wikipedia.org/wiki/Variable_shadowing) 具有相同名称的全局变量。

### [Scope constructs](@id man-scope-table)

引入作用域块的构造是：

| Construct                                                                        | Scope type   | Allowed within |
|:-------------------------------------------------------------------------------- |:------------ |:-------------- |
| [`module`](@ref), [`baremodule`](@ref)                                           | global       | global         |
| [`struct`](@ref)                                                                 | local (soft) | global         |
| [`for`](@ref), [`while`](@ref), [`try`](@ref try)                                | local (soft) | global, local  |
| [`macro`](@ref)                                                                  | local (hard) | global         |
| functions, [`do`](@ref) blocks, [`let`](@ref) blocks, comprehensions, generators | local (hard) | global, local  |

此表中显著缺失的是 [begin blocks](@ref man-compound-expressions) 和 [if blocks](@ref man-conditional-evaluation)，它们*不*引入新的作用域。这三种作用域遵循略有不同的规则，下面将进行解释。

Julia 使用 [lexical scoping](https://en.wikipedia.org/wiki/Scope_(computer_science)#Lexical_scope_vs._dynamic_scope)，这意味着一个函数的作用域并不继承自其调用者的作用域，而是继承自定义该函数的作用域。例如，在以下代码中，`foo` 内部的 `x` 指的是其模块 `Bar` 的全局作用域中的 `x`：

```jldoctest moduleBar
julia> module Bar
           x = 1
           foo() = x
       end;
```

并且在使用 `foo` 的范围内没有 `x`：

```jldoctest moduleBar
julia> import .Bar

julia> x = -1;

julia> Bar.foo()
1
```

因此，*词法作用域*意味着在特定代码片段中，变量所指的内容可以仅从其出现的代码中推断出来，而不依赖于程序的执行方式。嵌套在另一个作用域中的作用域可以“看到”其包含的所有外部作用域中的变量。另一方面，外部作用域无法看到内部作用域中的变量。

## Global Scope

每个模块引入一个新的全局作用域，与所有其他模块的全局作用域分开——没有一个包罗万象的全局作用域。模块可以通过 [using or import](@ref modules) 语句或通过使用点符号的合格访问将其他模块的变量引入其作用域，即每个模块都是一个所谓的 *命名空间*，同时也是一个将名称与值关联的第一类数据结构。

如果顶级表达式包含一个使用关键字 `local` 的变量声明，则该变量在该表达式外部不可访问。表达式内部的变量不会影响同名的全局变量。一个例子是在顶级的 `begin` 或 `if` 块中声明 `local x`：

```jldoctest
julia> x = 1
       begin
           local x = 0
           @show x
       end
       @show x;
x = 0
x = 1
```

请注意，交互式提示（即 REPL）位于模块 `Main` 的全局作用域中。

## [Local Scope](@id local-scope)

大多数代码块引入了一个新的局部作用域（请参见上面的 [table](@ref man-scope-table) 获取完整列表）。如果这样的代码块在另一个局部作用域内语法上嵌套，则它创建的作用域嵌套在它所出现的所有局部作用域内，这些局部作用域最终嵌套在代码被评估的模块的全局作用域内。外部作用域中的变量在它们包含的任何作用域中都是可见的——这意味着它们可以在内部作用域中被读取和写入——除非有一个同名的局部变量“遮蔽”了同名的外部变量。即使外部局部变量在内部块之后（在文本上方）声明，这一点也是成立的。当我们说一个变量在给定作用域中“存在”时，这意味着在当前作用域嵌套的任何作用域中都存在一个同名的变量，包括当前作用域。

某些编程语言要求在使用新变量之前显式声明它们。显式声明在 Julia 中也有效：在任何局部作用域中，写 `local x` 会在该作用域中声明一个新的局部变量，无论外部作用域中是否已经存在名为 `x` 的变量。然而，以这种方式声明每个新变量有点冗长和乏味，因此 Julia 和许多其他语言一样，认为对一个尚不存在的变量名进行赋值会隐式声明该变量。如果当前作用域是全局的，则新变量是全局的；如果当前作用域是局部的，则新变量是局部的，局限于最内层的局部作用域，并且在该作用域内可见，但在外部不可见。如果你对一个现有的局部变量进行赋值，它 *总是* 更新该现有的局部变量：你只能通过在嵌套作用域中显式声明一个新的局部变量并使用 `local` 关键字来遮蔽一个局部变量。特别地，这适用于在内部函数中赋值的变量，这可能会让来自 Python 的用户感到惊讶，因为在内部函数中的赋值会创建一个新的局部变量，除非该变量被显式声明为非局部。

大多数情况下，这非常直观，但与许多直观行为的事物一样，细节比人们天真想象的要微妙得多。

当 `x = <value>` 在局部作用域中出现时，Julia 根据赋值表达式出现的位置以及 `x` 在该位置已经指向的内容，应用以下规则来决定该表达式的含义：

1. **现有局部变量：** 如果 `x` 是 *已经是一个局部变量*，那么现有的局部变量 `x` 将被赋值；
2. **硬作用域：** 如果 `x` *不是已经是一个局部变量* 并且在任何硬作用域构造内发生赋值（即在 `let` 块、函数或宏体、推导或生成器内），则在赋值的作用域中创建一个名为 `x` 的新局部变量；
3. **软作用域：** 如果 `x` *不是一个局部变量* 并且包含赋值的所有作用域构造都是软作用域（循环、`try`/`catch` 块或 `struct` 块），则行为取决于全局变量 `x` 是否已定义：

      * 如果全局的 `x` 是 *未定义* 的，则在赋值的作用域中创建一个名为 `x` 的新局部变量；
      * 如果全局 `x` 是 *定义的*，则赋值被视为模糊：

          * 在 *非交互* 上下文中（文件、评估），会打印出模糊性警告，并创建一个新的局部变量；
          * 在 *交互式* 上下文中（REPL，笔记本），全局变量 `x` 被赋值。

您可能会注意到，在非交互式上下文中，硬作用域和软作用域的行为是相同的，唯一的区别是当一个隐式局部变量（即未使用 `local x` 声明的变量）遮蔽一个全局变量时，会打印出警告。在交互式上下文中，为了方便，规则遵循更复杂的启发式。这在后面的示例中有深入的讨论。

现在您知道规则了，让我们看一些示例。每个示例假定在一个新的 REPL 会话中进行评估，因此每个代码块中唯一的全局变量是该代码块中分配的变量。

我们将从一个简单明了的情况开始——在一个硬范围内的赋值，在这种情况下是一个函数体，当没有同名的局部变量已经存在时：

```jldoctest
julia> function greet()
           x = "hello" # new local
           println(x)
       end
greet (generic function with 1 method)

julia> greet()
hello

julia> x # global
ERROR: UndefVarError: `x` not defined in `Main`
```

在 `greet` 函数内部，赋值 `x = "hello"` 导致 `x` 成为函数作用域中的一个新局部变量。有两个相关的事实：赋值发生在局部作用域，并且没有现存的局部 `x` 变量。由于 `x` 是局部的，因此无论是否存在一个名为 `x` 的全局变量都无关紧要。这里举个例子，我们在定义和调用 `greet` 之前定义了 `x = 123`：

```jldoctest
julia> x = 123 # global
123

julia> function greet()
           x = "hello" # new local
           println(x)
       end
greet (generic function with 1 method)

julia> greet()
hello

julia> x # global
123
```

由于 `greet` 中的 `x` 是局部的，因此调用 `greet` 不会影响全局 `x` 的值（或缺失）。硬作用域规则不关心是否存在名为 `x` 的全局变量：在硬作用域中对 `x` 的赋值是局部的（除非 `x` 被声明为全局）。

下一个明确的情况是，当已经存在一个名为 `x` 的局部变量时，在这种情况下，`x = <value>` 总是将值赋给这个现有的局部 `x`。无论赋值发生在同一局部作用域、同一函数体内的内部局部作用域，还是在嵌套在另一个函数内部的函数体中，这都是正确的，也称为 [closure](https://en.wikipedia.org/wiki/Closure_(computer_programming))。

我们将使用 `sum_to` 函数，它计算从 1 到 `n` 的整数之和，作为一个例子：

```julia
function sum_to(n)
    s = 0 # new local
    for i = 1:n
        s = s + i # assign existing local
    end
    return s # same local
end
```

在前面的例子中，`sum_to` 顶部对 `s` 的第一次赋值使得 `s` 成为函数体内的新局部变量。`for` 循环在函数作用域内有其自己的内部局部作用域。在 `s = s + i` 发生的时刻，`s` 已经是一个局部变量，因此赋值更新了现有的 `s`，而不是创建一个新的局部变量。我们可以通过在 REPL 中调用 `sum_to` 来测试这一点：

```jldoctest
julia> function sum_to(n)
           s = 0 # new local
           for i = 1:n
               s = s + i # assign existing local
           end
           return s # same local
       end
sum_to (generic function with 1 method)

julia> sum_to(10)
55

julia> s # global
ERROR: UndefVarError: `s` not defined in `Main`
```

由于 `s` 是局部变量，属于函数 `sum_to`，调用该函数对全局变量 `s` 没有影响。我们还可以看到，在 `for` 循环中的更新 `s = s + i` 必须更新了由初始化 `s = 0` 创建的同一个 `s`，因为我们得到了从 1 到 10 的整数的正确和 55。

让我们深入探讨一下 `for` 循环体有其自己的作用域这一事实，通过编写一个稍微冗长的变体，我们称之为 `sum_to_def`，在其中我们在更新 `s` 之前将总和 `s + i` 保存到变量 `t` 中：

```jldoctest
julia> function sum_to_def(n)
           s = 0 # new local
           for i = 1:n
               t = s + i # new local `t`
               s = t # assign existing local `s`
           end
           return s, @isdefined(t)
       end
sum_to_def (generic function with 1 method)

julia> sum_to_def(10)
(55, false)
```

这个版本返回 `s` 和之前一样，但它还使用 `@isdefined` 宏来返回一个布尔值，指示在函数的最外层局部作用域中是否定义了名为 `t` 的局部变量。正如你所看到的，在 `for` 循环体外没有定义 `t`。这又是因为硬作用域规则：由于对 `t` 的赋值发生在一个函数内部，这引入了一个硬作用域，因此赋值使得 `t` 成为它出现的局部作用域中的一个新局部变量，即在循环体内。即使有一个名为 `t` 的全局变量，这也没有区别——硬作用域规则不受全局作用域中任何事物的影响。

请注意，for 循环体的局部作用域与内部函数的局部作用域没有区别。这意味着我们可以重写这个示例，使得循环体作为对内部辅助函数的调用来实现，并且它的行为是相同的：

```jldoctest
julia> function sum_to_def_closure(n)
           function loop_body(i)
               t = s + i # new local `t`
               s = t # assign same local `s` as below
           end
           s = 0 # new local
           for i = 1:n
               loop_body(i)
           end
           return s, @isdefined(t)
       end
sum_to_def_closure (generic function with 1 method)

julia> sum_to_def_closure(10)
(55, false)
```

这个例子说明了几个关键点：

1. 内部函数作用域就像任何其他嵌套的局部作用域。特别是，如果一个变量在内部函数外部已经是局部变量，并且你在内部函数中对其赋值，则外部局部变量会被更新。
2. 无论外部局部的定义是否发生在更新之前，规则保持不变。整个封闭的局部作用域在解析之前会被解析，并确定其局部变量，然后再解析内部局部的含义。

此设计意味着您通常可以在不改变其含义的情况下，将代码移入或移出内部函数，这促进了使用闭包的语言中许多常见习惯用法（请参见 [do blocks](@ref Do-Block-Syntax-for-Function-Arguments)）。

让我们继续讨论一些由软作用域规则涵盖的更模糊的案例。我们将通过将 `greet` 和 `sum_to_def` 函数的主体提取到软作用域上下文中来探索这一点。首先，让我们将 `greet` 的主体放入一个 `for` 循环中——这是软的，而不是硬的——并在 REPL 中评估它：

```jldoctest
julia> for i = 1:3
           x = "hello" # new local
           println(x)
       end
hello
hello
hello

julia> x
ERROR: UndefVarError: `x` not defined in `Main`
```

由于在评估 `for` 循环时全局 `x` 未定义，因此软作用域规则的第一个条款适用，`x` 被创建为 `for` 循环的局部变量，因此全局 `x` 在循环执行后仍然未定义。接下来，让我们考虑将 `sum_to_def` 的主体提取到全局作用域中，将其参数固定为 `n = 10`。

```julia
s = 0
for i = 1:10
    t = s + i
    s = t
end
s
@isdefined(t)
```

这段代码做了什么？提示：这是一个 trick 问题。答案是“这要看情况。”如果这段代码在交互式环境中输入，它的行为与在函数体内相同。但如果代码出现在文件中，它会打印出一个模糊性警告并抛出一个未定义变量错误。让我们先在 REPL 中看看它的工作情况：

```jldoctest
julia> s = 0 # global
0

julia> for i = 1:10
           t = s + i # new local `t`
           s = t # assign global `s`
       end

julia> s # global
55

julia> @isdefined(t) # global
false
```

REPL 通过判断循环内的赋值是赋给全局变量还是创建新的局部变量来近似函数体内的状态，这取决于是否定义了同名的全局变量。如果存在同名的全局变量，则赋值会更新该全局变量。如果不存在全局变量，则赋值会创建一个新的局部变量。在这个例子中，我们可以看到这两种情况的实际应用：

  * 没有全局命名为 `t`，因此 `t = s + i` 创建了一个在 `for` 循环中局部的 `t`；
  * 有一个全局变量 `s`，所以 `s = t` 将其赋值。

第二个事实是为什么循环的执行会改变全局变量 `s` 的值，第一个事实是为什么在循环执行后 `t` 仍然未定义。现在，让我们尝试将这段代码评估为在一个文件中：

```jldoctest
julia> code = """
       s = 0 # global
       for i = 1:10
           t = s + i # new local `t`
           s = t # new local `s` with warning
       end
       s, # global
       @isdefined(t) # global
       """;

julia> include_string(Main, code)
┌ Warning: Assignment to `s` in soft scope is ambiguous because a global variable by the same name exists: `s` will be treated as a new local. Disambiguate by using `local s` to suppress this warning or `global s` to assign to the existing global variable.
└ @ string:4
ERROR: LoadError: UndefVarError: `s` not defined in local scope
```

在这里，我们使用 [`include_string`](@ref) 来评估 `code`，就像它是一个文件的内容一样。我们也可以将 `code` 保存到一个文件中，然后在该文件上调用 `include`——结果将是相同的。正如你所看到的，这与在 REPL 中评估相同的代码表现得截然不同。让我们来分析一下这里发生了什么：

  * 全局 `s` 在循环评估之前被定义为 `0`
  * 赋值 `s = t` 发生在软作用域中——一个 `for` 循环外部，没有任何函数体或其他硬作用域结构。
  * 因此，软作用域规则的第二条款适用，赋值是模糊的，因此发出警告。
  * 执行继续，使 `s` 成为 `for` 循环体的局部变量
  * 由于 `s` 是 `for` 循环的局部变量，当评估 `t = s + i` 时，它是未定义的，从而导致错误。
  * 评估在此停止，但如果到达 `s` 并且 `@isdefined(t)`，它将返回 `0` 和 `false`。

这展示了一些作用域的重要方面：在一个作用域中，每个变量只能有一个含义，而这个含义是根据表达式的顺序来确定的。循环中表达式 `s = t` 的存在使得 `s` 成为循环的局部变量，这意味着当它出现在 `t = s + i` 的右侧时也是局部的，即使该表达式首先出现并首先被求值。人们可能会想象循环第一行的 `s` 可以是全局的，而第二行的 `s` 是局部的，但这是不可能的，因为这两行在同一个作用域块中，每个变量在给定的作用域中只能有一个含义。

#### [On Soft Scope](@id on-soft-scope)

我们现在已经涵盖了所有的局部作用域规则，但在结束这一部分之前，也许应该说几句关于为什么模糊的软作用域情况在交互式和非交互式上下文中处理方式不同。可以提出两个明显的问题：

1. 为什么它不能像 REPL 一样在任何地方工作？
2. 为什么它不能像在其他地方的文件中那样工作？也许可以跳过警告？

在 Julia ≤ 0.6 中，所有全局作用域的工作方式都像当前的 REPL：当在循环（或 `try`/`catch`，或 `struct` 体）中但在函数体（或 `let` 块或推导式）外部发生 `x = <value>` 时，是否定义了全局命名的 `x` 决定了 `x` 是否应该是局部于该循环。这种行为的优点在于直观和方便，因为它尽可能接近函数体内的行为。特别是，它使得在调试函数行为时，轻松地在函数体和 REPL 之间移动代码。然而，它也有一些缺点。首先，这是一种相当复杂的行为：多年来，许多人对这种行为感到困惑，并抱怨它复杂且难以解释和理解。这是一个合理的观点。其次，可能更糟的是，这对“大规模编程”是不利的。当你在一个地方看到一小段代码时，事情是相当清楚的：

```julia
s = 0
for i = 1:10
    s += i
end
```

显然，意图是修改现有的全局变量 `s`。还有什么其他的意思呢？然而，并不是所有的现实世界代码都是如此简短或清晰。我们发现，以下类似的代码在实际中经常出现：

```julia
x = 123

# much later
# maybe in a different file

for i = 1:10
    x = "hello"
    println(x)
end

# much later
# maybe in yet another file
# or maybe back in the first one where `x = 123`

y = x + 234
```

这里应该发生什么并不那么清楚。由于 `x + "hello"` 是一个方法错误，因此似乎意图是让 `x` 在 `for` 循环中是局部的。但是，运行时值和存在的方法不能用来确定变量的作用域。考虑到 Julia ≤ 0.6 的行为，尤其令人担忧的是，有人可能先写了 `for` 循环，并且运行得很好，但后来当其他人添加了一个新的全局变量——可能在不同的文件中——代码突然改变了含义，可能会发出噪音地崩溃，或者更糟的是，默默地做错了事情。这种 ["spooky action at a distance"](https://en.wikipedia.org/wiki/Action_at_a_distance_(computer_programming)) 是好的编程语言设计应该防止的事情。

在 Julia 1.0 中，我们简化了作用域的规则：在任何局部作用域中，对一个尚未是局部变量的名称的赋值会创建一个新的局部变量。这完全消除了软作用域的概念，并消除了潜在的神秘行为。由于去除软作用域，我们发现并修复了大量的错误，这证明了去除它的选择是正确的。大家都很高兴！嗯，不，实际上并不是。因为有些人对他们现在必须写的代码感到愤怒：

```julia
s = 0
for i = 1:10
    global s += i
end
```

你看到里面的 `global` 注解了吗？太可怕了。显然，这种情况是无法容忍的。但说真的，要求在这种顶层代码中使用 `global` 有两个主要问题：

1. 在函数体内复制和粘贴代码到 REPL 进行调试已不再方便——你必须添加 `global` 注释，然后再将其删除以返回；
2. 初学者会在没有 `global` 的情况下编写这种代码，并且不知道他们的代码为什么不工作——他们得到的错误是 `s` 未定义，这似乎并没有启发任何偶然犯这个错误的人。

截至 Julia 1.5，这段代码在 REPL 或 Jupyter 笔记本等交互式环境中可以在没有 `global` 注释的情况下正常工作（就像 Julia 0.6 一样），而在文件和其他非交互式环境中，它会打印出这个非常直接的警告：

> 在软作用域中对`s`的赋值是模糊的，因为存在一个同名的全局变量：`s`将被视为一个新的局部变量。通过使用`local s`来抑制此警告，或使用`global s`来赋值给现有的全局变量，以消除歧义。


这解决了这两个问题，同时保留了 1.0 行为的“规模化编程”好处：全局变量对可能远离的代码含义没有神秘的影响；在 REPL 中，复制和粘贴调试有效，初学者没有任何问题；每当有人忘记 `global` 注释或意外地在软作用域中用局部变量遮蔽现有全局变量时，尽管这会令人困惑，他们会收到一个清晰的警告。

这个设计的一个重要特性是，任何在没有警告的情况下在文件中执行的代码，在一个新的 REPL 中也会表现得相同。反之，如果你将一个 REPL 会话保存到文件中，如果它的行为与在 REPL 中的表现不同，那么你将会收到一个警告。

### Let Blocks

`let` 语句每次运行时都会创建一个新的 *硬作用域* 块（见上文）并引入新的变量绑定。变量不必立即赋值：

```jldoctest
julia> var1 = let x
           for i in 1:5
               (i == 4) && (x = i; break)
           end
           x
       end
4
```

虽然赋值可能会将新值重新分配给现有值的位置，但 `let` 始终会创建一个新位置。这个区别通常并不重要，只有在通过闭包超出其作用域的变量的情况下才能检测到。`let` 语法接受以逗号分隔的一系列赋值和变量名称：

```jldoctest
julia> x, y, z = -1, -1, -1;

julia> let x = 1, z
           println("x: $x, y: $y") # x is local variable, y the global
           println("z: $z") # errors as z has not been assigned yet but is local
       end
x: 1, y: -1
ERROR: UndefVarError: `z` not defined in local scope
```

赋值是按顺序进行评估的，每个右侧的表达式在引入左侧的新变量之前会在其作用域内进行评估。因此，写出类似 `let x = x` 的代码是有意义的，因为这两个 `x` 变量是不同的，并且有各自的存储空间。以下是一个需要 `let` 行为的示例：

```jldoctest
julia> Fs = Vector{Any}(undef, 2); i = 1;

julia> while i <= 2
           Fs[i] = ()->i
           global i += 1
       end

julia> Fs[1]()
3

julia> Fs[2]()
3
```

在这里，我们创建并存储两个闭包，它们返回变量 `i`。然而，它始终是同一个变量 `i`，因此这两个闭包的行为是相同的。我们可以使用 `let` 来为 `i` 创建一个新的绑定：

```jldoctest
julia> Fs = Vector{Any}(undef, 2); i = 1;

julia> while i <= 2
           let i = i
               Fs[i] = ()->i
           end
           global i += 1
       end

julia> Fs[1]()
1

julia> Fs[2]()
2
```

由于 `begin` 结构不会引入新的作用域，因此使用零参数的 `let` 仅引入一个新的作用域块而不立即创建任何新的绑定是很有用的：

```jldoctest
julia> let
           local x = 1
           let
               local x = 2
           end
           x
       end
1
```

由于 `let` 引入了一个新的作用域块，内部局部变量 `x` 与外部局部变量 `x` 是不同的变量。这个特定的例子等价于：

```jldoctest
julia> let x = 1
           let x = 2
           end
           x
       end
1
```

### Loops and Comprehensions

In loops and [comprehensions](@ref man-comprehensions), new variables introduced in their body scopes are freshly allocated for each loop iteration, as if the loop body were surrounded by a `let` block, as demonstrated by this example:

```jldoctest
julia> Fs = Vector{Any}(undef, 2);

julia> for j = 1:2
           Fs[j] = ()->j
       end

julia> Fs[1]()
1

julia> Fs[2]()
2
```

一个 `for` 循环或推导式迭代变量始终是一个新变量：

```julia-repl enable_doctest_when_deprecation_warning_is_removed
julia> function f()
           i = 0
           for i = 1:3
               # empty
           end
           return i
       end;

julia> f()
0
```

然而，有时重用现有的局部变量作为迭代变量是有用的。这可以通过添加关键字 `outer` 方便地实现：

```jldoctest
julia> function f()
           i = 0
           for outer i = 1:3
               # empty
           end
           return i
       end;

julia> f()
3
```

## Constants

一个常见的变量用法是为特定的、不变的值命名。这种变量只被赋值一次。可以使用 [`const`](@ref) 关键字将这种意图传达给编译器：

```jldoctest
julia> const e  = 2.71828182845904523536;

julia> const pi = 3.14159265358979323846;
```

可以在单个 `const` 语句中声明多个变量：

```jldoctest
julia> const a, b = 1, 2
(1, 2)
```

`const` 声明应仅在全局作用域中用于全局变量。由于全局变量的值（甚至类型）可能在几乎任何时候发生变化，因此编译器很难优化涉及全局变量的代码。如果一个全局变量不会改变，添加 `const` 声明可以解决这个性能问题。

局部常量是非常不同的。编译器能够自动确定何时局部变量是常量，因此局部常量声明不是必需的，实际上目前也不支持。

特殊的顶级赋值，例如由 `function` 和 `struct` 关键字执行的赋值，默认是常量。

请注意，`const` 仅影响变量绑定；变量可以绑定到一个可变对象（例如数组），并且该对象仍然可以被修改。此外，当尝试为声明为常量的变量赋值时，可能会出现以下情况：

  * 如果新值的类型与常量的类型不同，则会抛出错误：

```jldoctest
julia> const x = 1.0
1.0

julia> x = 1
ERROR: invalid redefinition of constant x
```

  * 如果新值与常量的类型相同，则会打印警告：

```jldoctest
julia> const y = 1.0
1.0

julia> y = 2.0
WARNING: redefinition of constant y. This may fail, cause incorrect answers, or produce other errors.
2.0
```

  * 如果赋值不会导致变量值的变化，则不会给出任何消息：

```jldoctest
julia> const z = 100
100

julia> z = 100
100
```

最后一条规则适用于不可变对象，即使变量绑定会改变，例如：

```julia-repl
julia> const s1 = "1"
"1"

julia> s2 = "1"
"1"

julia> pointer.([s1, s2], 1)
2-element Array{Ptr{UInt8},1}:
 Ptr{UInt8} @0x00000000132c9638
 Ptr{UInt8} @0x0000000013dd3d18

julia> s1 = s2
"1"

julia> pointer.([s1, s2], 1)
2-element Array{Ptr{UInt8},1}:
 Ptr{UInt8} @0x0000000013dd3d18
 Ptr{UInt8} @0x0000000013dd3d18
```

然而，对于可变对象，警告会如预期那样打印出来：

```jldoctest
julia> const a = [1]
1-element Vector{Int64}:
 1

julia> a = [1]
WARNING: redefinition of constant a. This may fail, cause incorrect answers, or produce other errors.
1-element Vector{Int64}:
 1
```

请注意，尽管有时可以更改 `const` 变量的值，但强烈不建议这样做，这仅仅是为了在交互使用时的方便。更改常量可能会导致各种问题或意外行为。例如，如果一个方法引用了一个常量，并且在常量更改之前已经编译，那么它可能会继续使用旧值：

```jldoctest
julia> const x = 1
1

julia> f() = x
f (generic function with 1 method)

julia> f()
1

julia> x = 2
WARNING: redefinition of constant x. This may fail, cause incorrect answers, or produce other errors.
2

julia> f()
1
```

## [Typed Globals](@id man-typed-globals)

!!! compat "Julia 1.8"
    在 Julia 1.8 中添加了对类型全局变量的支持


类似于被声明为常量，全局绑定也可以被声明为始终为常量类型。这可以通过使用语法 `global x::T` 在不分配实际值的情况下完成，或者在赋值时使用 `x::T = 123`。

```jldoctest
julia> x::Float64 = 2.718
2.718

julia> f() = x
f (generic function with 1 method)

julia> Base.return_types(f)
1-element Vector{Any}:
 Float64
```

对于任何赋值给全局变量，Julia 首先会尝试使用 [`convert`](@ref) 将其转换为适当的类型：

```jldoctest
julia> global y::Int

julia> y = 1.0
1.0

julia> y
1

julia> y = 3.14
ERROR: InexactError: Int64(3.14)
Stacktrace:
[...]
```

类型不需要是具体的，但使用抽象类型的注释通常对性能的提升有限。

一旦全局变量被分配或其类型被设置，绑定类型就不允许更改：

```jldoctest
julia> x = 1
1

julia> global x::Int
ERROR: cannot set type for global x. It already has a value or is already set to a different type.
Stacktrace:
[...]
```
