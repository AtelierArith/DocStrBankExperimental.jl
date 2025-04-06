# [StyledStrings](@id stdlib-styledstrings)

```@meta
CurrentModule = StyledStrings
DocTestSetup = quote
    using StyledStrings
end
```

!!! note
    StyledStrings 和 AnnotatedStrings 的 API 被视为实验性，并可能在 Julia 版本之间发生变化。


## [Styling](@id stdlib-styledstrings-styling)

在处理字符串时，格式化和样式通常被视为次要问题。

例如，当打印到终端时，您可能想在输出中添加 [ANSI escape sequences](https://en.wikipedia.org/wiki/ANSI_escape_code#SGR_(Select_Graphic_Rendition)_parameters)，在输出 HTML 样式构造（`<span style="...">` 等）时也有类似的目的，等等。可以简单地将原始样式构造插入到内容本身旁边的字符串中，但很快就会发现这并不适合除最基本用例之外的任何情况。并非所有终端都支持相同的 ANSI 代码，在计算已样式内容的宽度时需要小心翼翼地移除样式构造，而这还不包括处理多种输出格式。

为了不让这个头痛的问题在下游被广泛体验，它通过引入一种特殊的字符串类型（[`AnnotatedString`](@ref Base.AnnotatedString)）直接解决。该字符串类型包装了任何其他 [`AbstractString`](@ref) 类型，并允许将格式信息应用于特定区域（例如，第1到第7个字符为粗体和红色）。

字符串的区域通过应用 [`Face`](@ref StyledStrings.Face)（想想“字体”）来进行样式设置——一个包含样式信息的结构。为了方便，可以直接使用全局字体字典中的名称（例如 `shadow`），而不必直接给出 `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365`。

除了这些功能，我们还提供了一种方便的方式来构建 [`AnnotatedString`](@ref Base.AnnotatedString)，详细信息见 [Styled String Literals](@ref stdlib-styledstring-literals)。

```@repl demo
using StyledStrings
styled"{yellow:hello} {blue:there}"
```

## [Annotated Strings](@id man-annotated-strings)

有时能够持有与字符串区域相关的元数据是有用的。一个 [`AnnotatedString`](@ref Base.AnnotatedString) 包裹了另一个字符串，并允许对其区域进行带标签值的注释（`:label => value`）。所有通用字符串操作都应用于基础字符串。然而，当可能时，样式信息会被保留。这意味着你可以操作一个 `4d61726b646f776e2e436f64652822222c2022416e6e6f7461746564537472696e672229_4072656620426173652e416e6e6f7461746564537472696e67` —提取子字符串、填充它们、与其他字符串连接— 而元数据注释将“随之而来”。

这个字符串类型是 [StyledStrings stdlib](@ref stdlib-styledstrings) 的基础，它使用 `:face` 标签注释来保存样式信息。

在连接 [`AnnotatedString`](@ref Base.AnnotatedString) 时，请注意使用 [`annotatedstring`](@ref StyledStrings.annotatedstring) 而不是 [`string`](@ref)，如果您想保留字符串注释。

```jldoctest
julia> str = AnnotatedString("hello there", [(1:5, :word, :greeting), (7:11, :label, 1)])
"hello there"

julia> length(str)
11

julia> lpad(str, 14)
"   hello there"

julia> typeof(lpad(str, 7))
AnnotatedString{String}

julia> str2 = AnnotatedString(" julia", [(2:6, :face, :magenta)])
" julia"

julia> annotatedstring(str, str2)
"hello there julia"

julia> str * str2 == annotatedstring(str, str2) # *-concatenation works
true
```

[`AnnotatedString`](@ref Base.AnnotatedString) 的注释可以通过 [`annotations`](@ref StyledStrings.annotations) 和 [`annotate!`](@ref StyledStrings.annotate!) 函数进行访问和修改。

## Styling via [`AnnotatedString`](@ref Base.AnnotatedString)s

## [Faces](@id stdlib-styledstrings-faces)

### The `Face` type

一个 [`Face`](@ref StyledStrings.Face) 指定了文本可以设置的字体的详细信息。它涵盖了一组基本属性，这些属性在不同格式之间具有良好的通用性，即：

  * `字体`
  * `高度`
  * `体重`
  * `倾斜`
  * `前景`
  * `背景`
  * `下划线`
  * `删除线`
  * `反向`
  * `继承`

有关这些属性具体形式的详细信息，请参见 [`Face`](@ref StyledStrings.Face) 文档字符串，但特别值得关注的是 `inherit`，因为它允许您 *继承* 来自其他 `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` 的属性。

### The global faces dictionary

为了方便引用特定样式，存在一个全局的 `Dict{Symbol, Face}`，允许通过名称简单地引用 [`Face`](@ref StyledStrings.Face)。包可以通过 [`addface!`](@ref StyledStrings.addface!) 函数将面添加到此字典中，加载的面可以轻松 [customized](@ref stdlib-styledstrings-face-toml)。

!!! warning "Appropriate face naming"
    任何注册新面孔的包都应确保它们以包名为前缀，即遵循格式 `mypackage_myface`。这对于可预测性很重要，并且可以防止名称冲突。

    此外，软件包应注意使用（并引入）*语义*面孔（如 `code`）而不是直接的颜色和样式（如 `cyan`）。这在多个方面都是有帮助的，从使使用意图更加明显、帮助组合性到使用户自定义更加直观。


有两组对包前缀规则的豁免：

  * 默认值的面字典中包含的基本面集合
  * 由Julia自身的标准库引入的面孔，即`JuliaSyntaxHighlighting`

#### [Basic faces](@id stdlib-styledstrings-basic-faces)

基本面孔旨在代表一个广泛适用的一般概念。

对于设置某些具有特定属性的文本，我们有 `bold`、`light`、`italic`、`underline`、`strikethrough` 和 `inverse` 字体。

还有16种终端颜色的命名面：`black`、`red`、`green`、`yellow`、`blue`、`magenta`、`cyan`、`white`、`bright_black`/`grey`/`gray`、`bright_red`、`bright_green`、`bright_blue`、`bright_magenta`、`bright_cyan`和`bright_white`。

对于阴影文本（即暗淡但仍然可见），有 `shadow` 字体。为了指示选定区域，有 `region` 字体。类似地，强调和高亮的字体分别定义为 `emphasis` 和 `highlight`。还有 `code` 用于代码样式的文本。

为了直观地指示消息的严重性，定义了 `error`、`warning`、`success`、`info`、`note` 和 `tip` 面孔。

### [Customisation of faces (`Faces.toml`)](@id stdlib-styledstrings-face-toml)

在全球面孔字典中，名称面孔可自定义是好的。主题和美学很不错，这对可访问性也很重要。TOML 文件可以解析为一个 [`Face`](@ref StyledStrings.Face) 规范的列表，这些规范与面孔字典中现有条目合并。

一个 [`Face`](@ref StyledStrings.Face) 在 TOML 中表示如下：

```toml
[facename]
attribute = "value"
...

[package.facename]
attribute = "value"
```

例如，如果 `shadow` 面太难以阅读，可以像这样使其变得更亮：

```toml
[shadow]
foreground = "white"
```

在初始化时，首个 Julia 仓库下的 `config/faces.toml` 文件（通常是 `~/.julia`）会被加载。

### Applying faces to a `AnnotatedString`

根据约定，[`AnnotatedString`](@ref Base.AnnotatedString) 的 `:face` 属性包含当前适用的 [`Face`](@ref StyledStrings.Face) 的信息。这可以以多种形式给出，作为命名 `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` 的单个 `Symbol`，作为 `4d61726b646f776e2e436f64652822222c2022466163652229_40726566205374796c6564537472696e67732e46616365` 本身，或作为两者的向量。

`show(::IO, ::MIME"text/plain", ::AnnotatedString)` 和 `show(::IO, ::MIME"text/html", ::AnnotatedString)` 方法在确定整体样式时都会查看 `:face` 属性并将它们合并在一起。

我们可以在构造 `AnnotatedString` 时提供 `:face` 属性，之后将它们添加到属性列表中，或者使用方便的 [Styled String literals](@ref stdlib-styledstring-literals)。

```@repl demo
str1 = AnnotatedString("blue text", [(1:9, :face, :blue)])
str2 = styled"{blue:blue text}"
str1 == str2
sprint(print, str1, context = :color => true)
sprint(show, MIME("text/html"), str1, context = :color => true)
```

## [Styled String Literals](@id stdlib-styledstring-literals)

为了简化 [`AnnotatedString`](@ref Base.AnnotatedString) 的构建，应用 [`Face`](@ref StyledStrings.Face)，[`styled"..."`](@ref @styled_str) 风格的字符串字面量允许通过自定义语法轻松地将内容和属性一起表达。

在一个 [`styled"..."`](@ref @styled_str) 字面量中，大括号被视为特殊字符，在正常使用中必须转义（`\{`，`\}`）。这使得它们可以用于表达带有（可嵌套）`{annotations...:text}` 结构的注释。

`annotations...` 组件是三种类型注释的逗号分隔列表。

  * 面孔名称
  * 行内 `Face` 表达式 `(key=val,...)`
  * `键=值` 对

插值在所有地方都是可能的，除了内联面部关键帧。

有关语法的更多信息，请参阅 [`styled"..."`](@ref @styled_str) 文档字符串的扩展帮助。

作为示例，我们可以像这样演示上述提到的内置面孔列表：

```julia-repl
julia> println(styled"
The basic font-style attributes are {bold:bold}, {light:light}, {italic:italic},
{underline:underline}, and {strikethrough:strikethrough}.

In terms of color, we have named faces for the 16 standard terminal colors:
 {black:■} {red:■} {green:■} {yellow:■} {blue:■} {magenta:■} {cyan:■} {white:■}
 {bright_black:■} {bright_red:■} {bright_green:■} {bright_yellow:■} {bright_blue:■} {bright_magenta:■} {bright_cyan:■} {bright_white:■}

Since {code:bright_black} is effectively grey, we define two aliases for it:
{code:grey} and {code:gray} to allow for regional spelling differences.

To flip the foreground and background colors of some text, you can use the
{code:inverse} face, for example: {magenta:some {inverse:inverse} text}.

The intent-based basic faces are {shadow:shadow} (for dim but visible text),
{region:region} for selections, {emphasis:emphasis}, and {highlight:highlight}.
As above, {code:code} is used for code-like text.

Lastly, we have the 'message severity' faces: {error:error}, {warning:warning},
{success:success}, {info:info}, {note:note}, and {tip:tip}.

Remember that all these faces (and any user or package-defined ones) can
arbitrarily nest and overlap, {region,tip:like {bold,italic:so}}.")
```

```@raw comment
Documenter doesn't properly represent all the styling above, so I've converted it manually to HTML and LaTeX.
```

```@raw html
<pre>
 The basic font-style attributes are <span style="font-weight: 700;">bold</span>, <span style="font-weight: 300;">light</span>, <span style="font-style: italic;">italic</span>,
 <span style="text-decoration: underline;">underline</span>, and <span style="text-decoration: line-through">strikethrough</span>.

 In terms of color, we have named faces for the 16 standard terminal colors:
  <span style="color: #1c1a23;">■</span> <span style="color: #a51c2c;">■</span> <span style="color: #25a268;">■</span> <span style="color: #e5a509;">■</span> <span style="color: #195eb3;">■</span> <span style="color: #803d9b;">■</span> <span style="color: #0097a7;">■</span> <span style="color: #dddcd9;">■</span>
  <span style="color: #76757a;">■</span> <span style="color: #ed333b;">■</span> <span style="color: #33d079;">■</span> <span style="color: #f6d22c;">■</span> <span style="color: #3583e4;">■</span> <span style="color: #bf60ca;">■</span> <span style="color: #26c6da;">■</span> <span style="color: #f6f5f4;">■</span>

 Since <span style="color: #0097a7;">bright_black</span> is effectively grey, we define two aliases for it:
 <span style="color: #0097a7;">grey</span> and <span style="color: #0097a7;">gray</span> to allow for regional spelling differences.

 To flip the foreground and background colors of some text, you can use the
 <span style="color: #0097a7;">inverse</span> face, for example: <span style="color: #803d9b;">some </span><span style="background-color: #803d9b;">inverse</span><span style="color: #803d9b;"> text</span>.

 The intent-based basic faces are <span style="color: #76757a;">shadow</span> (for dim but visible text),
 <span style="background-color: #3a3a3a;">region</span> for selections, <span style="color: #195eb3;">emphasis</span>, and <span style="background-color: #195eb3;">highlight</span>.
 As above, <span style="color: #0097a7;">code</span> is used for code-like text.

 Lastly, we have the 'message severity' faces: <span style="color: #ed333b;">error</span>, <span style="color: #e5a509;">warning</span>,
 <span style="color: #25a268;">success</span>, <span style="color: #26c6da;">info</span>, <span style="color: #76757a;">note</span>, and <span style="color: #33d079;">tip</span>.

 Remember that all these faces (and any user or package-defined ones) can
 arbitrarily nest and overlap, <span style="color: #33d079;background-color: #3a3a3a;">like <span style="font-weight: 700;font-style: italic;">so</span></span>.</pre>
```

```@raw latex
\begingroup
\ttfamily
\setlength{\parindent}{0pt}
\setlength{\parskip}{\baselineskip}

The basic font-style attributes are {\fontseries{b}\selectfont bold}, {\fontseries{l}\selectfont light}, {\fontshape{it}\selectfont italic},\\
\underline{underline}, and {strikethrough}.

In terms of color, we have named faces for the 16 standard terminal colors:\\
{\color[HTML]{1c1a23}\(\blacksquare\)} {\color[HTML]{a51c2c}\(\blacksquare\)} {\color[HTML]{25a268}\(\blacksquare\)}
{\color[HTML]{e5a509}\(\blacksquare\)} {\color[HTML]{195eb3}\(\blacksquare\)} {\color[HTML]{803d9b}\(\blacksquare\)}
{\color[HTML]{0097a7}\(\blacksquare\)} {\color[HTML]{dddcd9}\(\blacksquare\)} \\
{\color[HTML]{76757a}\(\blacksquare\)} {\color[HTML]{ed333b}\(\blacksquare\)} {\color[HTML]{33d079}\(\blacksquare\)} {\color[HTML]{f6d22c}\(\blacksquare\)} {\color[HTML]{3583e4}\(\blacksquare\)} {\color[HTML]{bf60ca}\(\blacksquare\)} {\color[HTML]{26c6da}\(\blacksquare\)} {\color[HTML]{f6f5f4}\(\blacksquare\)}

Since {\color[HTML]{0097a7}bright\_black} is effectively grey, we define two aliases for it:\\
{\color[HTML]{0097a7}grey} and {\color[HTML]{0097a7}gray} to allow for regional spelling differences.

To flip the foreground and background colors of some text, you can use the\\
{\color[HTML]{0097a7}inverse} face, for example: {\color[HTML]{803d9b}some \colorbox[HTML]{803d9b}{\color[HTML]{000000}inverse} text}.

The intent-based basic faces are {\color[HTML]{76757a}shadow} (for dim but visible text),\\
\colorbox[HTML]{3a3a3a}{region} for selections, {\color[HTML]{195eb3}emphasis}, and \colorbox[HTML]{195eb3}{highlight}.\\
As above, {\color[HTML]{0097a7}code} is used for code-like text.

Lastly, we have the 'message severity' faces: {\color[HTML]{ed333b}error}, {\color[HTML]{e5a509}warning},\\
{\color[HTML]{25a268}success}, {\color[HTML]{26c6da}info}, {\color[HTML]{76757a}note}, and {\color[HTML]{33d079}tip}.

Remember that all these faces (and any user or package-defined ones) can\\
arbitrarily nest and overlap, \colorbox[HTML]{3a3a3a}{\color[HTML]{33d079}like
  {\fontseries{b}\fontshape{it}\selectfont so}}.
\endgroup
```

## [API reference](@id stdlib-styledstrings-api)

### Styling and Faces

```@docs
StyledStrings.@styled_str
StyledStrings.styled
StyledStrings.Face
StyledStrings.addface!
StyledStrings.withfaces
StyledStrings.SimpleColor
StyledStrings.parse(::Type{StyledStrings.SimpleColor}, ::String)
StyledStrings.tryparse(::Type{StyledStrings.SimpleColor}, ::String)
StyledStrings.merge(::StyledStrings.Face, ::StyledStrings.Face)
```
