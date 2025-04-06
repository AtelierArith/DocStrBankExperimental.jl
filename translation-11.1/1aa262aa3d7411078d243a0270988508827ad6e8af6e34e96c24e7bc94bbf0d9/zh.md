# [Strings](@id man-strings)

字符串是有限字符序列。当然，当人们问字符是什么时，真正的问题就来了。英语使用者熟悉的字符是字母 `A`、`B`、`C` 等，以及数字和常见的标点符号。这些字符通过 [ASCII](https://en.wikipedia.org/wiki/ASCII) 标准进行了标准化，并映射到 0 到 127 之间的整数值。当然，还有许多其他字符用于非英语语言，包括带有重音和其他修改的 ASCII 字符变体、相关的文字如西里尔字母和希腊字母，以及与 ASCII 和英语完全无关的文字，包括阿拉伯语、中文、希伯来语、印地语、日语和韩语。 [Unicode](https://en.wikipedia.org/wiki/Unicode) 标准解决了字符究竟是什么的复杂性，并被普遍接受为解决此问题的权威标准。根据您的需求，您可以完全忽略这些复杂性，假装只有 ASCII 字符存在，或者您可以编写能够处理在处理非 ASCII 文本时可能遇到的任何字符或编码的代码。Julia 使处理纯 ASCII 文本变得简单高效，处理 Unicode 也尽可能简单高效。特别是，您可以编写 C 风格的字符串代码来处理 ASCII 字符串，它们将在性能和语义方面按预期工作。如果这样的代码遇到非 ASCII 文本，它将优雅地失败，并给出清晰的错误信息，而不是默默地引入损坏的结果。当这种情况发生时，修改代码以处理非 ASCII 数据是直接的。

关于Julia字符串，有几个值得注意的高级特性：

  * 在 Julia 中，用于字符串（和字符串字面量）的内置具体类型是 [`String`](@ref)。这支持通过 [UTF-8](https://en.wikipedia.org/wiki/UTF-8) 编码的完整 [Unicode](https://en.wikipedia.org/wiki/Unicode) 字符。（提供了一个 [`transcode`](@ref) 函数来转换其他 Unicode 编码。）
  * 所有字符串类型都是抽象类型 `AbstractString` 的子类型，外部包定义了额外的 `AbstractString` 子类型（例如，用于其他编码）。如果您定义一个期望字符串参数的函数，您应该将类型声明为 `AbstractString` 以接受任何字符串类型。
  * 像 C 和 Java，但与大多数动态语言不同，Julia 有一个用于表示单个字符的第一类类型，称为 [`AbstractChar`](@ref)。内置的 [`Char`](@ref) 子类型 `AbstractChar` 是一种 32 位原始类型，可以表示任何 Unicode 字符（并且基于 UTF-8 编码）。
  * 在 Java 中，字符串是不可变的：`AbstractString` 对象的值不能被更改。要构造一个不同的字符串值，您需要从其他字符串的部分构造一个新的字符串。
  * 从概念上讲，字符串是一个*部分函数*，它将索引映射到字符：对于某些索引值，不会返回字符值，而是抛出异常。这允许通过编码表示的字节索引而不是字符索引高效地索引字符串，因为对于可变宽度的Unicode字符串，无法同时高效和简单地实现字符索引。

## [Characters](@id man-characters)

一个 `Char` 值表示一个单一字符：它只是一个 32 位原始类型，具有特殊的字面量表示和适当的算术行为，并且可以转换为一个数值，表示 [Unicode code point](https://en.wikipedia.org/wiki/Code_point)。（Julia 包可能定义其他 `AbstractChar` 的子类型，例如为了优化其他 [text encodings](https://en.wikipedia.org/wiki/Character_encoding) 的操作。）以下是 `Char` 值的输入和显示方式（请注意，字符字面量用单引号分隔，而不是双引号）：

```jldoctest
julia> c = 'x'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> typeof(c)
Char
```

您可以轻松地将 `Char` 转换为其整数值，即代码点：

```jldoctest
julia> c = Int('x')
120

julia> typeof(c)
Int64
```

在32位架构上，[`typeof(c)`](@ref) 将变为 [`Int32`](@ref)。你可以同样轻松地将整数值转换回 `Char`：

```jldoctest
julia> Char(120)
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)
```

并非所有整数值都是有效的 Unicode 代码点，但为了性能，`Char` 转换并不检查每个字符值是否有效。如果您想检查每个转换的值是否是有效的代码点，请使用 [`isvalid`](@ref) 函数：

```jldoctest
julia> Char(0x110000)
'\U110000': Unicode U+110000 (category In: Invalid, too high)

julia> isvalid(Char, 0x110000)
false
```

截至本文撰写时，有效的Unicode代码点是 `U+0000` 到 `U+D7FF` 以及 `U+E000` 到 `U+10FFFF`。这些代码点尚未全部分配可理解的含义，也不一定能被应用程序解释，但所有这些值都被视为有效的Unicode字符。

您可以使用 `\u` 后跟最多四个十六进制数字或 `\U` 后跟最多八个十六进制数字在单引号中输入任何 Unicode 字符（最长有效值只需要六个）：

```jldoctest
julia> '\u0'
'\0': ASCII/Unicode U+0000 (category Cc: Other, control)

julia> '\u78'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> '\u2200'
'∀': Unicode U+2200 (category Sm: Symbol, math)

julia> '\U10ffff'
'\U10ffff': Unicode U+10FFFF (category Cn: Other, not assigned)
```

Julia使用您系统的区域设置和语言设置来确定哪些字符可以原样打印，哪些必须使用通用的、转义的`\u`或`\U`输入形式输出。除了这些Unicode转义形式，所有的[C's traditional escaped input forms](https://en.wikipedia.org/wiki/C_syntax#Backslash_escapes)也可以使用：

```jldoctest
julia> Int('\0')
0

julia> Int('\t')
9

julia> Int('\n')
10

julia> Int('\e')
27

julia> Int('\x7f')
127

julia> Int('\177')
127
```

您可以对 `Char` 值进行比较和有限的算术运算：

```jldoctest
julia> 'A' < 'a'
true

julia> 'A' <= 'a' <= 'Z'
false

julia> 'A' <= 'X' <= 'Z'
true

julia> 'x' - 'a'
23

julia> 'A' + 1
'B': ASCII/Unicode U+0042 (category Lu: Letter, uppercase)
```

## String Basics

字符串字面量由双引号或三重双引号（而不是单引号）界定：

```jldoctest helloworldstring
julia> str = "Hello, world.\n"
"Hello, world.\n"

julia> """Contains "quote" characters"""
"Contains \"quote\" characters"
```

长字符串中的长行可以通过在换行符前加上反斜杠（`\`）来断开：

```jldoctest
julia> "This is a long \
       line"
"This is a long line"
```

如果你想从字符串中提取一个字符，你可以通过索引来实现：

```jldoctest helloworldstring
julia> str[begin]
'H': ASCII/Unicode U+0048 (category Lu: Letter, uppercase)

julia> str[1]
'H': ASCII/Unicode U+0048 (category Lu: Letter, uppercase)

julia> str[6]
',': ASCII/Unicode U+002C (category Po: Punctuation, other)

julia> str[end]
'\n': ASCII/Unicode U+000A (category Cc: Other, control)
```

许多 Julia 对象，包括字符串，可以用整数进行索引。第一个元素（字符串的第一个字符）的索引由 [`firstindex(str)`](@ref) 返回，最后一个元素（字符）的索引由 [`lastindex(str)`](@ref) 返回。关键字 `begin` 和 `end` 可以在索引操作中用作给定维度上第一个和最后一个索引的简写。字符串索引，像 Julia 中的大多数索引一样，是基于 1 的：`firstindex` 对于任何 `AbstractString` 总是返回 `1`。然而，正如我们下面将看到的，`lastindex(str)` 在一般情况下与 `length(str)` 对于字符串并不相同，因为某些 Unicode 字符可以占用多个“代码单元”。

您可以像处理普通值一样，对 [`end`](@ref) 执行算术和其他操作：

```jldoctest helloworldstring
julia> str[end-1]
'.': ASCII/Unicode U+002E (category Po: Punctuation, other)

julia> str[end÷2]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)
```

使用小于 `begin` (`1`) 或大于 `end` 的索引会引发错误：

```jldoctest helloworldstring
julia> str[begin-1]
ERROR: BoundsError: attempt to access 14-codeunit String at index [0]
[...]

julia> str[end+1]
ERROR: BoundsError: attempt to access 14-codeunit String at index [15]
[...]
```

您还可以使用范围索引提取子字符串：

```jldoctest helloworldstring
julia> str[4:9]
"lo, wo"
```

注意到表达式 `str[k]` 和 `str[k:k]` 并不返回相同的结果：

```jldoctest helloworldstring
julia> str[6]
',': ASCII/Unicode U+002C (category Po: Punctuation, other)

julia> str[6:6]
","
```

前者是类型为 `Char` 的单个字符值，而后者是恰好只包含一个字符的字符串值。在 Julia 中，这两者是非常不同的。

范围索引会复制原始字符串中选定的部分。或者，可以使用类型 [`SubString`](@ref) 创建对字符串的视图。更简单地说，使用 [`@views`](@ref) 宏在代码块上将所有字符串切片转换为子字符串。例如：

```jldoctest
julia> str = "long string"
"long string"

julia> substr = SubString(str, 1, 4)
"long"

julia> typeof(substr)
SubString{String}

julia> @views typeof(str[1:4]) # @views converts slices to SubStrings
SubString{String}
```

几个标准函数，如 [`chop`](@ref)、[`chomp`](@ref) 或 [`strip`](@ref) 返回 [`SubString`](@ref)。

## Unicode and UTF-8

Julia 完全支持 Unicode 字符和字符串。作为 [discussed above](@ref man-characters)，在字符字面量中，Unicode 代码点可以使用 Unicode `\u` 和 `\U` 转义序列表示，以及所有标准 C 转义序列。这些同样可以用于编写字符串字面量：

```jldoctest unicodestring
julia> s = "\u2200 x \u2203 y"
"∀ x ∃ y"
```

这些Unicode字符是以转义形式显示还是作为特殊字符显示，取决于您的终端的区域设置及其对Unicode的支持。字符串字面量使用UTF-8编码。UTF-8是一种可变宽度编码，这意味着并非所有字符都以相同数量的字节（“代码单元”）编码。在UTF-8中，ASCII字符——即代码点小于0x80（128）的字符——以ASCII中的形式编码，使用一个字节，而代码点0x80及以上的字符则使用多个字节编码——每个字符最多四个字节。

字符串索引在 Julia 中指的是代码单元（= UTF-8 的字节），这些是用于编码任意字符（代码点）的固定宽度构建块。这意味着并非每个对 `String` 的索引都一定是字符的有效索引。如果你在一个无效的字节索引处索引字符串，将会抛出一个错误：

```jldoctest unicodestring
julia> s[1]
'∀': Unicode U+2200 (category Sm: Symbol, math)

julia> s[2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[3]
ERROR: StringIndexError: invalid index [3], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[4]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)
```

在这种情况下，字符 `∀` 是一个三字节字符，因此索引 2 和 3 是无效的，下一个字符的索引是 4；这个下一个有效索引可以通过 [`nextind(s,1)`](@ref) 计算得出，之后的下一个索引可以通过 `nextind(s,4)` 计算，依此类推。

由于 `end` 始终是集合中最后一个有效索引，因此如果倒数第二个字符是多字节的，`end-1` 将引用一个无效的字节索引。

```jldoctest unicodestring
julia> s[end-1]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)

julia> s[end-2]
ERROR: StringIndexError: invalid index [9], valid nearby indices [7]=>'∃', [10]=>' '
Stacktrace:
[...]

julia> s[prevind(s, end, 2)]
'∃': Unicode U+2203 (category Sm: Symbol, math)
```

第一个案例有效，因为最后一个字符 `y` 和空格都是单字节字符，而 `end-2` 索引到 `∃` 多字节表示的中间。这个案例的正确方法是使用 `prevind(s, lastindex(s), 2)`，或者，如果你使用该值来索引 `s`，你可以写 `s[prevind(s, end, 2)]`，而 `end` 扩展为 `lastindex(s)`。

使用范围索引提取子字符串时，也需要有效的字节索引，否则会抛出错误：

```jldoctest unicodestring
julia> s[1:1]
"∀"

julia> s[1:2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[1:4]
"∀ "
```

由于可变长度编码，字符串中的字符数（由 [`length(s)`](@ref) 给出）并不总是与最后一个索引相同。如果你遍历索引 1 到 [`lastindex(s)`](@ref) 并索引到 `s`，当没有抛出错误时返回的字符序列就是组成字符串 `s` 的字符序列。因此 `length(s) <= lastindex(s)`，因为字符串中的每个字符必须有自己的索引。以下是一种低效且冗长的方式来遍历 `s` 的字符：

```jldoctest unicodestring
julia> for i = firstindex(s):lastindex(s)
           try
               println(s[i])
           catch
               # ignore the index error
           end
       end
∀

x

∃

y
```

空行实际上是有空格的。幸运的是，上述尴尬的习语在遍历字符串中的字符时并不必要，因为你可以直接将字符串用作可迭代对象，无需异常处理：

```jldoctest unicodestring
julia> for c in s
           println(c)
       end
∀

x

∃

y
```

如果您需要获取字符串的有效索引，可以使用 [`nextind`](@ref) 和 [`prevind`](@ref) 函数来递增/递减到下一个/上一个有效索引，如上所述。您还可以使用 [`eachindex`](@ref) 函数来遍历有效字符索引：

```jldoctest unicodestring
julia> collect(eachindex(s))
7-element Vector{Int64}:
  1
  4
  5
  6
  7
 10
 11
```

要访问编码的原始代码单元（UTF-8 的字节），您可以使用 [`codeunit(s,i)`](@ref) 函数，其中索引 `i` 从 `1` 连续运行到 [`ncodeunits(s)`](@ref)。 [`codeunits(s)`](@ref) 函数返回一个 `AbstractVector{UInt8}` 包装器，让您可以将这些原始代码单元（字节）作为数组访问。

在Julia中，字符串可以包含无效的UTF-8代码单元序列。这种约定允许将任何字节序列视为`String`。在这种情况下，规则是当从左到右解析代码单元序列时，字符是由与以下位模式之一的开头匹配的最长8位代码单元序列形成的（每个`x`可以是`0`或`1`）：

  * `0xxxxxxx`;
  * `110xxxxx` `10xxxxxx`;
  * `1110xxxx` `10xxxxxx` `10xxxxxx`;
  * `11110xxx` `10xxxxxx` `10xxxxxx` `10xxxxxx`;
  * `10xxxxxx`;
  * `11111xxx`.

特别是，这意味着过长和过高的代码单元序列及其前缀被视为一个单一的无效字符，而不是多个无效字符。这个规则可以通过一个例子来最好地解释：

```julia-repl
julia> s = "\xc0\xa0\xe2\x88\xe2|"
"\xc0\xa0\xe2\x88\xe2|"

julia> foreach(display, s)
'\xc0\xa0': [overlong] ASCII/Unicode U+0020 (category Zs: Separator, space)
'\xe2\x88': Malformed UTF-8 (category Ma: Malformed, bad data)
'\xe2': Malformed UTF-8 (category Ma: Malformed, bad data)
'|': ASCII/Unicode U+007C (category Sm: Symbol, math)

julia> isvalid.(collect(s))
4-element BitArray{1}:
 0
 0
 0
 1

julia> s2 = "\xf7\xbf\xbf\xbf"
"\U1fffff"

julia> foreach(display, s2)
'\U1fffff': Unicode U+1FFFFF (category In: Invalid, too high)
```

我们可以看到字符串 `s` 中的前两个代码单元形成了一个过长的空格字符编码。它是无效的，但在字符串中被接受为一个单一字符。接下来的两个代码单元形成了一个有效的三字节 UTF-8 序列的开始。然而，第五个代码单元 `\xe2` 不是其有效的延续。因此，代码单元 3 和 4 也被解释为这个字符串中的格式错误字符。同样，代码单元 5 形成了一个格式错误的字符，因为 `|` 不是它的有效延续。最后，字符串 `s2` 包含一个过高的代码点。

Julia 默认使用 UTF-8 编码，并且可以通过包添加对新编码的支持。例如，[LegacyStrings.jl](https://github.com/JuliaStrings/LegacyStrings.jl) 包实现了 `UTF16String` 和 `UTF32String` 类型。关于其他编码的进一步讨论以及如何实现对它们的支持超出了本文档的范围。有关 UTF-8 编码问题的进一步讨论，请参见下面关于 [byte array literals](@ref man-byte-array-literals) 的部分。提供了 [`transcode`](@ref) 函数，以在各种 UTF-xx 编码之间转换数据，主要用于处理外部数据和库。

## [Concatenation](@id man-concatenation)

最常见和有用的字符串操作之一是连接：

```jldoctest stringconcat
julia> greet = "Hello"
"Hello"

julia> whom = "world"
"world"

julia> string(greet, ", ", whom, ".\n")
"Hello, world.\n"
```

重要的是要意识到潜在的危险情况，例如无效 UTF-8 字符串的连接。结果字符串可能包含与输入字符串不同的字符，并且其字符数可能低于连接字符串字符数的总和，例如：

```julia-repl
julia> a, b = "\xe2\x88", "\x80"
("\xe2\x88", "\x80")

julia> c = string(a, b)
"∀"

julia> collect.([a, b, c])
3-element Vector{Vector{Char}}:
 ['\xe2\x88']
 ['\x80']
 ['∀']

julia> length.([a, b, c])
3-element Vector{Int64}:
 1
 1
 1
```

这种情况只会发生在无效的 UTF-8 字符串中。对于有效的 UTF-8 字符串，连接操作会保留字符串中的所有字符，并且字符串长度的可加性得以保持。

Julia 还提供 [`*`](@ref) 用于字符串连接：

```jldoctest stringconcat
julia> greet * ", " * whom * ".\n"
"Hello, world.\n"
```

虽然 `*` 对于使用 `+` 进行字符串连接的语言用户来说可能看起来是一个令人惊讶的选择，但这种 `*` 的用法在数学中，特别是在抽象代数中，有其先例。

在数学中，`+` 通常表示一种 *交换* 操作，其中操作数的顺序无关紧要。一个例子是矩阵加法，对于任何形状相同的矩阵 `A` 和 `B`，都有 `A + B == B + A`。相反，`*` 通常表示一种 *非交换* 操作，其中操作数的顺序 *是* 重要的。一个例子是矩阵乘法，通常情况下 `A * B != B * A`。与矩阵乘法一样，字符串连接也是非交换的：`greet * whom != whom * greet`。因此，`*` 是一个更自然的选择，作为中缀字符串连接运算符，与常见的数学用法一致。

更准确地说，所有有限长度字符串 *S* 的集合以及字符串连接运算符 `*` 形成一个 [free monoid](https://en.wikipedia.org/wiki/Free_monoid) (*S*, `*`)。该集合的单位元素是空字符串 `""`。每当一个自由幺半群不是交换的时，运算通常用 `\cdot`、`*` 或类似符号表示，而不是 `+`，因为如前所述，`+` 通常暗示交换性。

## [Interpolation](@id string-interpolation)

构造字符串时使用连接可能会变得有些繁琐。为了减少对这些冗长调用的需求，例如 [`string`](@ref) 或重复的乘法，Julia 允许在字符串字面量中使用 `$` 进行插值，类似于 Perl：

```jldoctest
julia> greet = "Hello"; whom = "world";

julia> "$greet, $whom.\n"
"Hello, world.\n"
```

这更易读且方便，相当于上述字符串连接——系统将这个明显的单字符串字面量重写为调用 `string(greet, ", ", whom, ".\n")`。

在 `$` 之后，最短的完整表达式被视为要插入字符串中的值的表达式。因此，您可以使用括号将任何表达式插入字符串中：

```jldoctest
julia> "1 + 2 = $(1 + 2)"
"1 + 2 = 3"
```

连接和字符串插值都调用 [`string`](@ref) 将对象转换为字符串形式。然而，`string` 实际上只是返回 [`print`](@ref) 的输出，因此新类型应该向 `4d61726b646f776e2e436f64652822222c20227072696e742229_40726566` 或 [`show`](@ref) 添加方法，而不是 `string`。

大多数非`AbstractString`对象被转换为字符串，紧密对应于它们作为字面表达式输入的方式：

```jldoctest
julia> v = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> "v: $v"
"v: [1, 2, 3]"
```

[`string`](@ref) 是 `AbstractString` 和 `AbstractChar` 值的标识，因此它们被插入到字符串中时，保持原样，不加引号和转义：

```jldoctest
julia> c = 'x'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> "hi, $c"
"hi, x"
```

要在字符串字面量中包含一个字面量的 `$`，请用反斜杠进行转义：

```jldoctest
julia> print("I have \$100 in my account.\n")
I have $100 in my account.
```

## Triple-Quoted String Literals

当使用三重引号（`"""..."""`）创建字符串时，它们具有一些特殊的行为，这对于创建较长的文本块非常有用。

首先，三重引号字符串也会缩进到最少缩进行的级别。这对于在缩进的代码中定义字符串非常有用。例如：

```jldoctest
julia> str = """
           Hello,
           world.
         """
"  Hello,\n  world.\n"
```

在这种情况下，关闭 `"""` 之前的最后一行（空行）设置了缩进级别。

缩进级别是通过所有行中最长的公共起始空格或制表符序列来确定的，排除开头 `"""` 后的行以及仅包含空格或制表符的行（包含关闭 `"""` 的行始终包括在内）。然后，对于所有行，排除开头 `"""` 后的文本，公共起始序列被移除（包括如果它们以此序列开头的仅包含空格和制表符的行），例如：

```jldoctest
julia> """    This
         is
           a test"""
"    This\nis\n  a test"
```

接下来，如果开头的 `"""` 后面跟着一个换行符，则该换行符会从结果字符串中去除。

```julia
"""hello"""
```

等价于

```julia
"""
hello"""
```

但

```julia
"""

hello"""
```

将包含一个字面换行符在开头。

去除换行符是在去缩进后执行的。例如：

```jldoctest
julia> """
         Hello,
         world."""
"Hello,\nworld."
```

如果使用反斜杠移除换行，缩进也会被尊重：

```jldoctest
julia> """
         Averylong\
         word"""
"Averylongword"
```

尾随空格保持不变。

三重引号字符串字面量可以包含 `"` 字符而无需转义。

请注意，在字面字符串中，无论是单引号还是三引号，换行都会在字符串中产生一个换行符（LF）字符 `\n`，即使您的编辑器使用回车符 `\r`（CR）或 CRLF 组合来结束行。要在字符串中包含 CR，请使用显式转义 `\r`；例如，您可以输入字面字符串 `"a CRLF line ending\r\n"`。

## Common Operations

您可以使用标准比较运算符按字典顺序比较字符串：

```jldoctest
julia> "abracadabra" < "xylophone"
true

julia> "abracadabra" == "xylophone"
false

julia> "Hello, world." != "Goodbye, world."
true

julia> "1 + 2 = 3" == "1 + 2 = $(1 + 2)"
true
```

您可以使用 [`findfirst`](@ref) 和 [`findlast`](@ref) 函数搜索特定字符的索引：

```jldoctest
julia> findfirst('o', "xylophone")
4

julia> findlast('o', "xylophone")
7

julia> findfirst('z', "xylophone")
```

您可以通过使用函数 [`findnext`](@ref) 和 [`findprev`](@ref) 在给定的偏移量处开始搜索字符：

```jldoctest
julia> findnext('o', "xylophone", 1)
4

julia> findnext('o', "xylophone", 5)
7

julia> findprev('o', "xylophone", 5)
4

julia> findnext('o', "xylophone", 8)
```

您可以使用 [`occursin`](@ref) 函数来检查子字符串是否在字符串中：

```jldoctest
julia> occursin("world", "Hello, world.")
true

julia> occursin("o", "Xylophon")
true

julia> occursin("a", "Xylophon")
false

julia> occursin('o', "Xylophon")
true
```

最后一个例子表明 [`occursin`](@ref) 也可以查找字符字面量。

另外两个实用的字符串函数是 [`repeat`](@ref) 和 [`join`](@ref)：

```jldoctest
julia> repeat(".:Z:.", 10)
".:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:."

julia> join(["apples", "bananas", "pineapples"], ", ", " and ")
"apples, bananas and pineapples"
```

其他一些有用的功能包括：

  * [`firstindex(str)`](@ref) 给出了可以用于索引 `str` 的最小（字节）索引（对于字符串始终为 1，但对于其他容器不一定成立）。
  * [`lastindex(str)`](@ref) 给出了可以用于索引 `str` 的最大（字节）索引。
  * [`length(str)`](@ref) 中的字符数量为 64。
  * [`length(str, i, j)`](@ref) 在 `str` 中从 `i` 到 `j` 的有效字符索引数量。
  * [`ncodeunits(str)`](@ref) 数量为 [code units](https://en.wikipedia.org/wiki/Character_encoding#Terminology) 在字符串中。
  * [`codeunit(str, i)`](@ref) 在字符串 `str` 的索引 `i` 处给出代码单元值。
  * [`thisind(str, i)`](@ref) given an arbitrary index into a string find the first index of the character into which the index points.
  * [`nextind(str, i, n=1)`](@ref) 找到在索引 `i` 之后的第 `n` 个字符的起始位置。
  * [`prevind(str, i, n=1)`](@ref) 在索引 `i` 之前找到第 `n` 个字符的起始位置。

## [Non-Standard String Literals](@id non-standard-string-literals)

在某些情况下，您可能想构造一个字符串或使用字符串语义，但标准字符串构造的行为并不完全符合需求。对于这些情况，Julia 提供了非标准字符串字面量。非标准字符串字面量看起来像一个常规的双引号字符串字面量，但前面会立即加上一个标识符，并且可能与普通字符串字面量的行为不同。

[Regular expressions](@ref man-regex-literals)、[byte array literals](@ref man-byte-array-literals) 和 [version number literals](@ref man-version-number-literals)，如下面所述，是一些非标准字符串字面量的示例。用户和包也可以定义新的非标准字符串字面量。更多文档请参见 [Metaprogramming](@ref meta-non-standard-string-literals) 部分。

## [Regular Expressions](@id man-regex-literals)

有时你并不是在寻找一个确切的字符串，而是一个特定的 *模式*。例如，假设你正在尝试从一个大型文本文件中提取一个单一的日期。你不知道那个日期是什么（这就是你在寻找它的原因），但你确实知道它的格式看起来像 `YYYY-MM-DD`。正则表达式允许你指定这些模式并进行搜索。

Julia 使用版本 2 的 Perl 兼容正则表达式（regex），由 [PCRE](https://www.pcre.org/) 库提供（有关更多详细信息，请参见 [PCRE2 syntax description](https://www.pcre.org/current/doc/html/pcre2syntax.html)）。正则表达式与字符串有两种关系：显而易见的联系是正则表达式用于在字符串中查找规律模式；另一种联系是正则表达式本身作为字符串输入，这些字符串被解析成一个状态机，可以用来高效地在字符串中搜索模式。在 Julia 中，正则表达式使用以 `r` 开头的各种标识符前缀的非标准字符串字面量输入。最基本的正则表达式字面量在没有任何选项开启的情况下仅使用 `r"..."`：

```jldoctest
julia> re = r"^\s*(?:#|$)"
r"^\s*(?:#|$)"

julia> typeof(re)
Regex
```

要检查正则表达式是否匹配字符串，请使用 [`occursin`](@ref)：

```jldoctest
julia> occursin(r"^\s*(?:#|$)", "not a comment")
false

julia> occursin(r"^\s*(?:#|$)", "# a comment")
true
```

如您所见，[`occursin`](@ref) 仅返回 true 或 false，指示给定的正则表达式在字符串中是否匹配。然而，通常人们不仅想知道字符串是否匹配，还想知道 *如何* 匹配。要捕获有关匹配的信息，请使用 [`match`](@ref) 函数：

```jldoctest
julia> match(r"^\s*(?:#|$)", "not a comment")

julia> match(r"^\s*(?:#|$)", "# a comment")
RegexMatch("#")
```

如果正则表达式不匹配给定的字符串，[`match`](@ref) 返回 [`nothing`](@ref) – 一个特殊值，不会在交互提示符中打印。除了不打印，它是一个完全正常的值，您可以通过编程方式进行测试：

```julia
m = match(r"^\s*(?:#|$)", line)
if m === nothing
    println("not a comment")
else
    println("blank or comment")
end
```

如果正则表达式匹配成功，[`match`](@ref) 返回的值是一个 [`RegexMatch`](@ref) 对象。这些对象记录了表达式的匹配情况，包括模式匹配的子字符串和任何捕获的子字符串（如果有的话）。这个例子只捕获了匹配的子字符串部分，但也许我们想要捕获注释字符后面的任何非空文本。我们可以这样做：

```jldoctest
julia> m = match(r"^\s*(?:#\s*(.*?)\s*$)", "# a comment ")
RegexMatch("# a comment ", 1="a comment")
```

当调用 [`match`](@ref) 时，您可以选择一个索引来开始搜索。例如：

```jldoctest
julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",1)
RegexMatch("1")

julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",6)
RegexMatch("2")

julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",11)
RegexMatch("3")
```

您可以从 `RegexMatch` 对象中提取以下信息：

  * 整个匹配的子字符串：`m.match`
  * 捕获的子字符串作为字符串数组：`m.captures`
  * 整个匹配开始的偏移量：`m.offset`
  * 捕获子字符串的偏移量作为一个向量：`m.offsets`

对于当捕获不匹配时，`m.captures` 在该位置包含 `nothing`，而 `m.offsets` 的偏移量为零（请记住，Julia 中的索引是从 1 开始的，因此字符串中的零偏移量是无效的）。以下是两个有些牵强的示例：

```jldoctest acdmatch
julia> m = match(r"(a|b)(c)?(d)", "acd")
RegexMatch("acd", 1="a", 2="c", 3="d")

julia> m.match
"acd"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "a"
 "c"
 "d"

julia> m.offset
1

julia> m.offsets
3-element Vector{Int64}:
 1
 2
 3

julia> m = match(r"(a|b)(c)?(d)", "ad")
RegexMatch("ad", 1="a", 2=nothing, 3="d")

julia> m.match
"ad"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "a"
 nothing
 "d"

julia> m.offset
1

julia> m.offsets
3-element Vector{Int64}:
 1
 0
 2
```

将捕获结果作为数组返回是很方便的，这样可以使用解构语法将它们绑定到局部变量。为了方便起见，`RegexMatch` 对象实现了迭代器方法，这些方法会传递到 `captures` 字段，因此您可以直接解构匹配对象：

```jldoctest acdmatch
julia> first, second, third = m; first
"a"
```

捕获也可以通过使用捕获组的编号或名称对 `RegexMatch` 对象进行索引来访问：

```jldoctest
julia> m=match(r"(?<hour>\d+):(?<minute>\d+)","12:45")
RegexMatch("12:45", hour="12", minute="45")

julia> m[:minute]
"45"

julia> m[2]
"45"
```

捕获可以在使用 [`replace`](@ref) 的替换字符串中通过使用 `\n` 来引用第 n 个捕获组，并且用 `s` 前缀替换字符串。捕获组 0 指的是整个匹配对象。命名捕获组可以在替换中用 `\g<groupname>` 引用。例如：

```jldoctest
julia> replace("first second", r"(\w+) (?<agroup>\w+)" => s"\g<agroup> \1")
"second first"
```

编号捕获组也可以通过 `\g<n>` 进行引用以消除歧义，如下所示：

```jldoctest
julia> replace("a", r"." => s"\g<0>1")
"a1"
```

您可以通过在闭合双引号后添加一些组合的标志 `i`、`m`、`s` 和 `x` 来修改正则表达式的行为。这些标志的含义与 Perl 中相同，如以下摘录所述：[perlre manpage](https://perldoc.perl.org/perlre#Modifiers)。

```
i   Do case-insensitive pattern matching.

    If locale matching rules are in effect, the case map is taken
    from the current locale for code points less than 255, and
    from Unicode rules for larger code points. However, matches
    that would cross the Unicode rules/non-Unicode rules boundary
    (ords 255/256) will not succeed.

m   Treat string as multiple lines.  That is, change "^" and "$"
    from matching the start or end of the string to matching the
    start or end of any line anywhere within the string.

s   Treat string as single line.  That is, change "." to match any
    character whatsoever, even a newline, which normally it would
    not match.

    Used together, as r""ms, they let the "." match any character
    whatsoever, while still allowing "^" and "$" to match,
    respectively, just after and just before newlines within the
    string.

x   Tells the regular expression parser to ignore most whitespace
    that is neither backslashed nor within a character class. You
    can use this to break up your regular expression into
    (slightly) more readable parts. The '#' character is also
    treated as a metacharacter introducing a comment, just as in
    ordinary code.
```

例如，以下正则表达式的所有三个标志都已开启：

```jldoctest
julia> r"a+.*b+.*d$"ism
r"a+.*b+.*d$"ims

julia> match(r"a+.*b+.*d$"ism, "Goodbye,\nOh, angry,\nBad world\n")
RegexMatch("angry,\nBad world")
```

`r"..."` 字面量是在没有插值和反转义的情况下构造的（除了引号 `"` 仍然需要转义）。以下是一个显示与标准字符串字面量之间差异的示例：

```julia-repl
julia> x = 10
10

julia> r"$x"
r"$x"

julia> "$x"
"10"

julia> r"\x"
r"\x"

julia> "\x"
ERROR: syntax: invalid escape sequence
```

三重引号的正则表达式字符串，形式为 `r"""..."""`，也被支持（并且对于包含引号或换行符的正则表达式可能很方便）。

`Regex()` 构造函数可以用于以编程方式创建有效的正则表达式字符串。这允许在构建正则表达式字符串时使用字符串变量的内容和其他字符串操作。上述任何正则表达式代码都可以在 `Regex()` 的单个字符串参数中使用。以下是一些示例：

```jldoctest
julia> using Dates

julia> d = Date(1962,7,10)
1962-07-10

julia> regex_d = Regex("Day " * string(day(d)))
r"Day 10"

julia> match(regex_d, "It happened on Day 10")
RegexMatch("Day 10")

julia> name = "Jon"
"Jon"

julia> regex_name = Regex("[\"( ]\\Q$name\\E[\") ]")  # interpolate value of name
r"[\"( ]\QJon\E[\") ]"

julia> match(regex_name, " Jon ")
RegexMatch(" Jon ")

julia> match(regex_name, "[Jon]") === nothing
true
```

注意使用 `\Q...\E` 转义序列。`\Q` 和 `\E` 之间的所有字符都被解释为字面字符。这对于匹配否则会被视为正则表达式元字符的字符非常方便。然而，在与字符串插值一起使用此功能时需要谨慎，因为插值字符串本身可能包含 `\E` 序列，从而意外终止字面匹配。在将用户输入包含在正则表达式中之前，需要对其进行清理。

## [Byte Array Literals](@id man-byte-array-literals)

另一个有用的非标准字符串字面量是字节数组字符串字面量：`b"..."`。这种形式允许您使用字符串表示法来表示只读字面字节数组——即 [`UInt8`](@ref) 值的数组。这些对象的类型是 `CodeUnits{UInt8, String}`。字节数组字面量的规则如下：

  * ASCII字符和ASCII转义产生一个字节。
  * `\x` 和八进制转义序列生成与转义值对应的 *字节*。
  * Unicode 转义序列生成一个字节序列，该字节序列以 UTF-8 编码该代码点。

这些规则之间有一些重叠，因为 `\x` 的行为和小于 0x80（128）的八进制转义都被前两条规则涵盖，但在这里这些规则是一致的。总的来说，这些规则允许人们轻松使用 ASCII 字符、任意字节值和 UTF-8 序列来生成字节数组。以下是一个使用这三者的示例：

```jldoctest
julia> b"DATA\xff\u2200"
8-element Base.CodeUnits{UInt8, String}:
 0x44
 0x41
 0x54
 0x41
 0xff
 0xe2
 0x88
 0x80
```

ASCII 字符串 "DATA" 对应的字节为 68, 65, 84, 65。 `\xff` 产生单个字节 255。Unicode 转义 `\u2200` 在 UTF-8 中编码为三个字节 226, 136, 128。请注意，结果字节数组不对应有效的 UTF-8 字符串：

```jldoctest
julia> isvalid("DATA\xff\u2200")
false
```

正如所提到的，`CodeUnits{UInt8, String}` 类型表现得像只读的 `UInt8` 数组，如果你需要一个标准向量，可以使用 `Vector{UInt8}` 进行转换：

```jldoctest
julia> x = b"123"
3-element Base.CodeUnits{UInt8, String}:
 0x31
 0x32
 0x33

julia> x[1]
0x31

julia> x[1] = 0x32
ERROR: CanonicalIndexError: setindex! not defined for Base.CodeUnits{UInt8, String}
[...]

julia> Vector{UInt8}(x)
3-element Vector{UInt8}:
 0x31
 0x32
 0x33
```

还要注意 `\xff` 和 `\uff` 之间的显著区别：前者转义序列编码的是 *字节 255*，而后者转义序列表示的是 *代码点 255*，在 UTF-8 中编码为两个字节：

```jldoctest
julia> b"\xff"
1-element Base.CodeUnits{UInt8, String}:
 0xff

julia> b"\uff"
2-element Base.CodeUnits{UInt8, String}:
 0xc3
 0xbf
```

字符字面量使用相同的行为。

对于小于 `\u80` 的代码点，UTF-8 编码的每个代码点恰好是由相应的 `\x` 转义产生的单个字节，因此可以安全地忽略这种区别。然而，对于 `\x80` 到 `\xff` 的转义与 `\u80` 到 `\uff` 的转义之间，存在一个主要区别：前者的转义全部编码为单字节，除非后面跟着非常特定的继续字节，否则这些字节不形成有效的 UTF-8 数据，而后者的转义全部表示具有双字节编码的 Unicode 代码点。

如果这一切都让人感到极其困惑，试着阅读 ["The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets"](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)。这是对Unicode和UTF-8的极好介绍，可能有助于缓解一些关于此事的困惑。

## [Version Number Literals](@id man-version-number-literals)

版本号可以很容易地用非标准字符串字面量表示，形式为 [`v"..."`](@ref @v_str)。版本号字面量创建 [`VersionNumber`](@ref) 对象，这些对象遵循 [semantic versioning](https://semver.org/) 的规范，因此由主要、次要和补丁数字值组成，后面跟着预发布和构建的字母数字注释。例如，`v"0.2.1-rc1+win64"` 被分解为主要版本 `0`、次要版本 `2`、补丁版本 `1`、预发布 `rc1` 和构建 `win64`。在输入版本字面量时，除了主要版本号之外，其他所有内容都是可选的，因此例如 `v"0.2"` 等同于 `v"0.2.0"`（带有空的预发布/构建注释），`v"2"` 等同于 `v"2.0.0"`，依此类推。

`VersionNumber` 对象主要用于轻松且正确地比较两个（或多个）版本。例如，常量 [`VERSION`](@ref) 将 Julia 版本号作为 `VersionNumber` 对象，因此可以使用简单的语句定义一些特定版本的行为，如：

```julia
if v"0.2" <= VERSION < v"0.3-"
    # do something specific to 0.2 release series
end
```

注意，在上述示例中使用了非标准版本号 `v"0.3-"`，并带有一个尾随的 `-`：这种表示法是 Julia 对标准的扩展，用于指示一个低于任何 `0.3` 版本的版本，包括其所有的预发布版本。因此，在上述示例中，代码仅能在稳定的 `0.2` 版本上运行，并排除诸如 `v"0.3.0-rc1"` 的版本。为了也允许不稳定（即预发布）`0.2` 版本，下限检查应修改为：`v"0.2-" <= VERSION`。

另一个非标准版本规范扩展允许使用尾随的 `+` 来表示构建版本的上限，例如 `VERSION > v"0.2-rc1+"` 可以表示任何高于 `0.2-rc1` 的版本及其任何构建：对于版本 `v"0.2-rc1+win64"` 将返回 `false`，而对于 `v"0.2-rc2"` 将返回 `true`。

在比较中使用这种特殊版本是一个好习惯（特别是，除非有充分的理由，否则上限总是应该使用尾随的 `-`），但它们不能作为任何事物的实际版本号，因为它们在语义版本控制方案中是无效的。

除了用于 [`VERSION`](@ref) 常量外，`VersionNumber` 对象在 `Pkg` 模块中被广泛使用，以指定软件包版本及其依赖关系。

## [Raw String Literals](@id man-raw-string-literals)

原始字符串不进行插值或解码，可以用非标准字符串字面量的形式 `raw"..."` 表示。原始字符串字面量创建普通的 `String` 对象，这些对象包含所输入的内容，完全没有插值或解码。这对于包含使用 `$` 或 `\` 作为特殊字符的其他语言中的代码或标记的字符串非常有用。

例外情况是引号仍然必须被转义，例如 `raw"\""` 等价于 `"\""`. 为了能够表达所有字符串，反斜杠也必须被转义，但仅在出现在引号字符之前时：

```jldoctest
julia> println(raw"\\ \\\"")
\\ \"
```

注意到前两个反斜杠在输出中逐字出现，因为它们不在引号字符之前。然而，下一个反斜杠字符转义了紧随其后的反斜杠，而最后一个反斜杠转义了一个引号，因为这些反斜杠出现在引号之前。

## [Annotated Strings](@id man-annotated-strings)

!!! note
    AnnotatedStrings 的 API 被视为实验性，并可能在 Julia 版本之间发生变化。


有时能够持有与字符串区域相关的元数据是有用的。一个 [`AnnotatedString`](@ref Base.AnnotatedString) 包裹了另一个字符串，并允许对其区域进行带标签值的注释（`:label => value`）。所有通用字符串操作都应用于基础字符串。然而，当可能时，样式信息会被保留。这意味着你可以操作一个 `4d61726b646f776e2e436f64652822222c2022416e6e6f7461746564537472696e672229_4072656620426173652e416e6e6f7461746564537472696e67` —提取子字符串、填充它们、与其他字符串连接— 而元数据注释将“随之而来”。

这个字符串类型是 [StyledStrings stdlib](@ref stdlib-styledstrings) 的基础，它使用 `:face` 标签注释来保存样式信息。

在连接 [`AnnotatedString`](@ref Base.AnnotatedString) 时，请注意使用 [`annotatedstring`](@ref Base.annotatedstring) 而不是 [`string`](@ref)，如果您想保留字符串注释。

```jldoctest
julia> str = Base.AnnotatedString("hello there",
               [(1:5, :word, :greeting), (7:11, :label, 1)])
"hello there"

julia> length(str)
11

julia> lpad(str, 14)
"   hello there"

julia> typeof(lpad(str, 7))
Base.AnnotatedString{String}

julia> str2 = Base.AnnotatedString(" julia", [(2:6, :face, :magenta)])
" julia"

julia> Base.annotatedstring(str, str2)
"hello there julia"

julia> str * str2 == Base.annotatedstring(str, str2) # *-concatenation still works
true
```

[`AnnotatedString`](@ref Base.AnnotatedString) 的注释可以通过 [`annotations`](@ref Base.annotations) 和 [`annotate!`](@ref Base.annotate!) 函数进行访问和修改。
