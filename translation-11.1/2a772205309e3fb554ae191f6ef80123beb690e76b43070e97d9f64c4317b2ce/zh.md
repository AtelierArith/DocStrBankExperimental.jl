```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Markdown/docs/src/index.md"
```

# [Markdown](@id markdown_stdlib)

本节描述了Julia的Markdown语法，该语法由Markdown标准库启用。支持以下Markdown元素：

## Inline elements

这里“内联”指的是可以在文本块中找到的元素，即段落。这些元素包括以下内容。

### Bold

用两个星号`**`包围单词，以将所包含的文本显示为粗体。

```
A paragraph containing a **bold** word.
```

### Italics

用一个星号 `*` 包围单词，以将括起来的文本显示为斜体。

```
A paragraph containing an *italicized* word.
```

### Literals

用单个反引号 ``` ` ``` 包围应按原样显示的文本。

```
A paragraph containing a `literal` word.
```

在编写引用变量、函数或其他 Julia 程序部分名称的文本时，应使用字面量。

!!! tip
    要在文字中包含反引号字符，请使用三个反引号而不是一个来包围文本。

    ```
    A paragraph containing ``` `backtick` characters ```.
    ```

    通过扩展，任何奇数个反引号都可以用来包围较少数量的反引号。


### $\LaTeX$

用双反引号 ``` `` ``` 包围应以数学形式显示的文本，使用 $\LaTeX$ 语法。

```
A paragraph containing some ``\LaTeX`` markup.
```

!!! tip
    与前一节中的文字相同，如果需要在双反引号内写入文字反引号，则使用大于两个的偶数。请注意，如果需要在 $\LaTeX$ 标记中包含一个单独的文字反引号，则两个封闭的反引号就足够了。


!!! note
    在Julia源代码中，如果文本嵌入在字符串中，`\`字符应适当地转义，例如，```"``\\LaTeX`` 在文档字符串中的语法。"```，因为它被解释为字符串字面量。或者，为了避免转义，可以使用`raw`字符串宏与`@doc`宏一起使用：

    ```
    @doc raw"``\LaTeX`` syntax in a docstring." functionname
    ```


### Links

链接到外部或内部目标可以使用以下语法编写，其中方括号 `[ ]` 中的文本是链接的名称，圆括号 `( )` 中的文本是 URL。

```
A paragraph containing a link to [Julia](https://www.julialang.org).
```

在Julia文档中，也可以添加对其他已记录的函数/方法/变量的交叉引用。例如：

```julia
"""
    tryparse(type, str; base)

Like [`parse`](@ref), but returns either a value of the requested type,
or [`nothing`](@ref) if the string does not contain a valid number.
"""
```

这将在生成的文档中创建一个指向 [`parse`](@ref) 文档的链接（该文档提供了有关此函数实际功能的更多信息），以及指向 [`nothing`](@ref) 文档的链接。包含对变异/非变异版本函数的交叉引用，或突出两个看似相似函数之间的差异是很好的做法。

!!! note
    上述交叉引用*不是*Markdown特性，而是依赖于[Documenter.jl](https://github.com/JuliaDocs/Documenter.jl)，该链接用于构建基础Julia的文档。


### Footnote references

命名和编号的脚注引用可以使用以下语法编写。脚注名称必须是一个不包含标点符号的单一字母数字单词。

```
A paragraph containing a numbered footnote [^1] and a named one [^named].
```

!!! note
    脚注相关的文本可以在同一页面的任何位置书写，脚注引用的语法在下面的 [Footnotes](@ref) 部分中讨论。


## Toplevel elements

以下元素可以在文档的“顶层”或另一个“顶层”元素中编写。

### Paragraphs

段落是一块纯文本，可能包含在上述 [Inline elements](@ref) 部分定义的任意数量的内联元素，上下有一个或多个空行。

```
This is a paragraph.

And this is *another* paragraph containing some emphasized text.
A new line, but still part of the same paragraph.
```

### Headers

文档可以使用标题分成不同的部分。标题使用以下语法：

```julia
# Level One
## Level Two
### Level Three
#### Level Four
##### Level Five
###### Level Six
```

标题行可以像段落一样包含任何行内语法。

!!! tip
    尽量避免在单个文档中使用过多级别的标题。一个层次过于嵌套的文档可能表明需要对其进行重组或将其拆分为几个涵盖不同主题的页面。


### Code blocks

源代码可以通过缩进四个空格或一个制表符以文字块的形式显示，如下例所示。

```
This is a paragraph.

    function func(x)
        # ...
    end

Another paragraph.
```

此外，代码块可以使用三个反引号括起来，并可选择性地指定“语言”以指明代码块应如何高亮显示。

````
A code block without a "language":

```
function func(x)
    # ...
end
```

and another one with the "language" specified as `julia`:

```julia
function func(x)
    # ...
end
```
````

!!! note
    “围栏”代码块，如最后一个示例所示，应优先于缩进代码块，因为没有办法指定缩进代码块所用的语言。


### Block quotes

从外部来源引用的文本，例如书籍或网站的引用，可以使用 `>` 字符在引用的每一行前面添加，如下所示。

```
Here's a quote:

> Julia is a high-level, high-performance dynamic programming language for
> technical computing, with syntax that is familiar to users of other
> technical computing environments.
```

注意在每行的 `>` 字符后面必须有一个空格。引用块本身可以包含其他顶级或内联元素。

### Images

图像的语法与上述提到的链接语法类似。在链接前加上 `!` 字符将显示来自指定 URL 的图像，而不是链接。

```julia
![alternative text](link/to/image.png)
```

### Lists

无序列表可以通过在列表中的每个项目之前添加 `*`、`+` 或 `-` 来编写。

```
A list of items:

  * item one
  * item two
  * item three
```

注意每个 `*` 前面的两个空格和后面的一个空格。

列表可以包含其他嵌套的顶级元素，例如列表、代码块或引用块。在列表中包含任何顶级元素时，应在每个列表项之间留出空行。

```
Another list:

  * item one

  * item two

    ```
    f(x) = x
    ```

  * And a sublist:

      + sub-item one
      + sub-item two
```

!!! note
    每个列表项的内容必须与该项的第一行对齐。在上面的示例中，围栏代码块必须缩进四个空格，以与“item two”中的“i”对齐。


有序列表是通过用正整数替换“项目符号”字符（即 `*`、`+` 或 `-`），后面跟上 `.` 或 `)` 来书写的。

```
Two ordered lists:

 1. item one
 2. item two
 3. item three

 5) item five
 6) item six
 7) item seven
```

一个有序列表可以从一个不是一的数字开始，如上例中的第二个列表，它从五开始。与无序列表一样，有序列表可以包含嵌套的顶级元素。

### Display equations

大型 $\LaTeX$ 方程式如果无法在段落内行内显示，可以使用带有 "language" `math` 的围栏代码块作为显示方程式，如下面的示例所示。

````julia
```math
f(a) = \frac{1}{2\pi}\int_{0}^{2\pi} (\alpha+R\cos(\theta))d\theta
```
````

### Footnotes

此语法与 [Footnote references](@ref) 的行内语法配对。确保也阅读该部分。

脚注文本使用以下语法定义，这与脚注引用语法相似，除了在脚注标签后附加的 `:` 字符。

```
[^1]: Numbered footnote text.

[^note]:

    Named footnote text containing several toplevel elements
    indented by 4 spaces or one tab.

      * item one
      * item two
      * item three

    ```julia
    function func(x)
        # ...
    end
    ```
```

!!! note
    在解析过程中不会进行检查，以确保所有脚注引用都有匹配的脚注。


### Horizontal rules

使用三个连字符（`---`）可以实现与`<hr>` HTML标签等效的效果。例如：

```
Text above the line.

---

And text below the line.
```

### Tables

基本表格可以使用下面描述的语法编写。请注意，Markdown 表格的功能有限，不能包含嵌套的顶级元素，与上述讨论的其他元素不同——只允许内联元素。表格必须始终包含一个带有列名的标题行。单元格不能跨越表格的多行或多列。

```
| Column One | Column Two | Column Three |
|:---------- | ---------- |:------------:|
| Row `1`    | Column `2` |              |
| *Row* 2    | **Row** 2  | Column ``3`` |
```

!!! note
    如上例所示，每列的 `|` 字符必须垂直对齐。

    在列标题分隔符的两端出现 `:` 字符指定了该列的对齐方式：如果在一端有 `:`，则该列左对齐；如果在另一端有 `:`，则该列右对齐；如果两端都有 `:`，则该列居中对齐。如果没有提供 `:` 字符，则默认右对齐该列。


### Admonitions

特别格式化的块，称为警告，可以用来突出特定的备注。它们可以使用以下 `!!!` 语法定义：

```
!!! note

    This is the content of the note.
    It is indented by 4 spaces. A tab would work as well.

!!! warning "Beware!"

    And this is another one.

    This warning admonition has a custom title: `"Beware!"`.
```

`!!!` 后的第一个词声明了警告的类型。有标准的警告类型应产生特殊的样式。即（按严重性递减的顺序）：`danger`、`warning`、`info`/`note` 和 `tip`。

您还可以使用您自己的警告类型，只要类型名称仅包含小写拉丁字符（a-z）。例如，您可以有一个 `terminology` 块，如下所示：

```
!!! terminology "julia vs Julia"

    Strictly speaking, "Julia" refers to the language,
    and "julia" to the standard implementation.
```

然而，除非渲染 Markdown 的代码对该特定警告类型进行了特殊处理，否则它将获得默认样式。

可以在警告类型后提供一个自定义标题作为字符串（用双引号括起来）。如果在警告类型后未指定标题文本，则将使用类型名称作为标题（例如，对于 `note` 警告，标题为 `"Note"`）。

警告和大多数其他顶级元素一样，可以包含其他顶级元素（例如列表、图像）。

## [Markdown String Literals](@id stdlib-markdown-literals)

`md""` 宏允许您将 Markdown 字符串直接嵌入到您的 Julia 代码中。此宏旨在简化在您的 Julia 源文件中包含 Markdown 格式文本的过程。

### Usage

```julia
result = md"This is a **custom** Markdown string with [a link](http://example.com)."
```

## Markdown Syntax Extensions

Julia 的 Markdown 支持插值，方式与基本字符串字面量非常相似，区别在于它会将对象本身存储在 Markdown 树中（而不是将其转换为字符串）。当渲染 Markdown 内容时，将调用通常的 `show` 方法，并且这些方法可以像往常一样被重写。这种设计允许 Markdown 扩展任意复杂的特性（例如引用），而不会使基本语法变得杂乱。

原则上，Markdown 解析器本身也可以通过包进行任意扩展，或者可以使用完全自定义的 Markdown 风格，但通常这并不是必要的。

## [API reference](@id stdlib-markdown-api)

```@docs
Markdown.MD
Markdown.@md_str
Markdown.@doc_str
Markdown.html
Markdown.latex
```
