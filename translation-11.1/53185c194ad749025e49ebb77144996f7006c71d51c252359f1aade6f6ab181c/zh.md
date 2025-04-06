# [Variables](@id man-variables)

在Julia中，变量是与一个值关联（或绑定）的名称。当你想要存储一个值（例如，你在某些数学运算后获得的值）以便后续使用时，它是非常有用的。例如：

```julia-repl
# Assign the value 10 to the variable x
julia> x = 10
10

# Doing math with x's value
julia> x + 1
11

# Reassign x's value
julia> x = 1 + 1
2

# You can assign values of other types, like strings of text
julia> x = "Hello World!"
"Hello World!"
```

Julia 提供了一个极其灵活的变量命名系统。变量名是区分大小写的，并且没有语义意义（也就是说，语言不会根据变量的名称对其进行不同的处理）。

```jldoctest
julia> x = 1.0
1.0

julia> y = -3
-3

julia> Z = "My string"
"My string"

julia> customary_phrase = "Hello world!"
"Hello world!"

julia> UniversalDeclarationOfHumanRightsStart = "人人生而自由，在尊严和权利上一律平等。"
"人人生而自由，在尊严和权利上一律平等。"
```

Unicode 名称（以 UTF-8 编码）是允许的：

```jldoctest
julia> δ = 0.00001
1.0e-5

julia> 안녕하세요 = "Hello"
"Hello"
```

在 Julia REPL 和其他几个 Julia 编辑环境中，您可以通过输入反斜杠后跟 LaTeX 符号名称并按下 Tab 键来输入许多 Unicode 数学符号。例如，变量名 `δ` 可以通过输入 `\delta`-*tab* 来输入，甚至 `α̂⁽²⁾` 可以通过 `\alpha`-*tab*-`\hat`-*tab*-`\^(2)`-*tab* 来输入。（如果您在某处找到一个符号，例如在其他人的代码中，而您不知道如何输入，REPL 帮助会告诉您：只需输入 `?` 然后粘贴该符号。）

Julia 甚至允许你用本地常量和函数覆盖现有的导出常量和函数（尽管不推荐这样做，以避免潜在的混淆）：

```jldoctest; filter = r"with \d+ methods"
julia> pi = 3
3

julia> pi
3

julia> sqrt = 4
4

julia> length() = 5
length (generic function with 1 method)

julia> Base.length
length (generic function with 79 methods)
```

然而，如果你尝试重新定义一个已经在使用的内置常量或函数，Julia 会给你一个错误：

```jldoctest
julia> pi
π = 3.1415926535897...

julia> pi = 3
ERROR: cannot assign a value to imported variable Base.pi from module Main

julia> sqrt(100)
10.0

julia> sqrt = 4
ERROR: cannot assign a value to imported variable Base.sqrt from module Main
```

## [Allowed Variable Names](@id man-allowed-variable-names)

变量名必须以字母（A-Z 或 a-z）、下划线或大于 00A0 的 Unicode 代码点的子集开头；特别是 [Unicode character categories](https://www.fileformat.info/info/unicode/category/index.htm) Lu/Ll/Lt/Lm/Lo/Nl（字母）、Sc/So（货币和其他符号）以及一些其他类似字母的字符（例如，Sm 数学符号的子集）是允许的。后续字符还可以包括 ! 和数字（0-9 以及 Nd/No 类别中的其他字符），以及其他 Unicode 代码点：变音符号和其他修饰符（Mn/Mc/Me/Sk 类别）、一些标点连接符（Pc 类别）、撇号和其他一些字符。

运算符如 `+` 也是有效的标识符，但会被特殊解析。在某些上下文中，运算符可以像变量一样使用；例如，`(+)` 指的是加法函数，而 `(+) = f` 将重新赋值给它。大多数 Unicode 中缀运算符（在 Sm 类别中），如 `⊕`，被解析为中缀运算符，并可用于用户定义的方法（例如，你可以使用 `const ⊗ = kron` 将 `⊗` 定义为中缀克罗内克积）。运算符也可以带有修饰符、撇号和下标/上标，例如 `+̂ₐ″` 被解析为具有与 `+` 相同优先级的中缀运算符。运算符后面带有下标/上标字母时，必须在运算符和后续变量名之间留有空格。例如，如果 `+ᵃ` 是一个运算符，则 `+ᵃx` 必须写作 `+ᵃ x` 以将其与 `+ ᵃx` 区分开来，其中 `ᵃx` 是变量名。

一种特定的变量名类是仅包含下划线的变量名。这些标识符是只写的。即，它们只能被赋值，这些值会立即被丢弃，并且它们的值无法以任何方式使用。

```julia-repl
julia> x, ___ = size([2 2; 1 1])
(2, 2)

julia> y = ___
ERROR: syntax: all-underscore identifiers are write-only and their values cannot be used in expressions

julia> println(___)
ERROR: syntax: all-underscore identifiers are write-only and their values cannot be used in expressions
```

The only explicitly disallowed names for variables are the names of the built-in [Keywords](@ref Keywords):

```julia-repl
julia> else = false
ERROR: syntax: unexpected "else"

julia> try = "No"
ERROR: syntax: unexpected "="
```

一些Unicode字符在标识符中被视为等效。输入Unicode组合字符（例如，重音符号）的不同方式被视为等效（具体来说，Julia标识符是 [NFC](https://en.wikipedia.org/wiki/Unicode_equivalence)。Julia还包括一些非标准的等效字符，这些字符在视觉上相似，并且通过某些输入法容易输入。Unicode字符 `ɛ` (U+025B: 拉丁小写字母开放e) 和 `µ` (U+00B5: 微符号) 被视为与相应的希腊字母等效。中点 `·` (U+00B7) 和希腊字母 [interpunct](https://en.wikipedia.org/wiki/Interpunct) `·` (U+0387) 都被视为数学点运算符 `⋅` (U+22C5)。减号 `−` (U+2212) 被视为与连字符减号 `-` (U+002D) 等效。

## [Assignment expressions and assignment versus mutation](@id man-assignment-expressions)

一个赋值 `variable = value` 将名称 `variable` 绑定到右侧计算出的 `value`，整个赋值在 Julia 中被视为等于右侧 `value` 的表达式。这意味着赋值可以被 *链接*（将相同的 `value` 赋值给多个变量，例如 `variable1 = variable2 = value`）或用于其他表达式，这也是为什么它们的结果在 REPL 中显示为右侧的值。（一般来说，REPL 显示您评估的任何表达式的值。）例如，这里 `b = 2+2` 的值 `4` 被用于另一个算术操作和赋值：

```jldoctest
julia> a = (b = 2+2) + 3
7

julia> a
7

julia> b
4
```

一个常见的混淆是*赋值*（给一个值一个新的“名称”）和*变异*（改变一个值）之间的区别。如果你运行 `a = 2` 然后运行 `a = 3`，你已经将“名称” `a` 改为指向一个新的值 `3` ……你并没有改变数字 `2`，所以 `2+2` 仍然会得到 `4` 而不是 `6`！当处理像 [arrays](@ref lib-arrays) 这样的*可变*类型时，这种区别变得更加清晰，因为它的内容*可以*被改变：

```jldoctest mutation_vs_rebind
julia> a = [1,2,3] # an array of 3 integers
3-element Vector{Int64}:
 1
 2
 3

julia> b = a   # both b and a are names for the same array!
3-element Vector{Int64}:
 1
 2
 3
```

这里，行 `b = a` 并*不*复制数组 `a`，它只是将名称 `b` 绑定到*同一个*数组 `a`：`b` 和 `a` 都“指向”内存中的一个数组 `[1,2,3]`。相反，赋值 `a[i] = value` *改变*了数组的*内容*，修改后的数组将通过名称 `a` 和 `b` 都可见：

```jldoctest mutation_vs_rebind
julia> a[1] = 42     # change the first element
42

julia> a = 3.14159   # a is now the name of a different object
3.14159

julia> b   # b refers to the original array object, which has been mutated
3-element Vector{Int64}:
 42
  2
  3
```

也就是说，`a[i] = value`（[`setindex!`](@ref) 的别名）*变更*了内存中现有的数组对象，可以通过 `a` 或 `b` 访问。随后设置 `a = 3.14159` 并不会改变这个数组，它只是将 `a` 绑定到一个不同的对象；这个数组仍然可以通过 `b` 访问。另一种常见的语法来变更现有对象是 `a.field = value`（[`setproperty!`](@ref) 的别名），可以用来改变一个 [`mutable struct`](@ref)。 还有通过点赋值进行变更，例如 `b .= 5:7`（这会就地变更我们的数组 `b` 使其包含 `[5,6,7]`），作为 Julia 的 [vectorized "dot" syntax](@ref man-dot-operators) 的一部分。

当你在 Julia 中调用一个 [function](@ref man-functions) 时，它的行为就像你*将*参数值分配给与函数参数对应的新变量名，正如在 [Argument-Passing Behavior](@ref man-argument-passing) 中讨论的那样。 （通过 [convention](@ref man-punctuation)，那些改变一个或多个参数的函数的名称以 `!` 结尾。）

## Stylistic Conventions

虽然 Julia 对有效名称的限制很少，但采用以下约定已变得很有用：

  * 变量的名称为小写。
  * 单词分隔可以通过下划线（`'_'`）来表示，但除非名称难以阅读，否则不鼓励使用下划线。
  * `Type`和`Module`的名称以大写字母开头，单词分隔使用大驼峰命名法而不是下划线。
  * 函数和宏的名称使用小写字母，不带下划线。
  * 以 `!` 结尾的函数名称表示这些函数会对其参数进行写操作。这些函数有时被称为“变异”或“就地”函数，因为它们旨在在函数调用后对其参数进行更改，而不仅仅是返回一个值。

有关风格规范的更多信息，请参见 [Style Guide](@ref)。
