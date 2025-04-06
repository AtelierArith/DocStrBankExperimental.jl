```
Unicode.normalize(s::AbstractString; keywords...)
Unicode.normalize(s::AbstractString, normalform::Symbol)
```

规范化字符串 `s`。默认情况下，执行规范组合（`compose=true`），而不确保 Unicode 版本稳定性（`compat=false`），这会生成尽可能短的等效字符串，但可能会引入在早期 Unicode 版本中不存在的组合字符。

或者，可以指定 Unicode 标准的四种“规范形式”之一：`normalform` 可以是 `:NFC`、`:NFD`、`:NFKC` 或 `:NFKD`。 规范形式 C（规范组合）和 D（规范分解）将相同抽象字符串的不同视觉上相同的表示转换为单一的规范形式，其中形式 C 更加紧凑。 规范形式 KC 和 KD 还额外规范化“兼容等价物”：它们将抽象上相似但视觉上不同的字符转换为单一的规范选择（例如，它们将连字扩展为单个字符），其中形式 KC 更加紧凑。

或者，可以通过调用 `Unicode.normalize(s; keywords...)` 来获得更细粒度的控制和额外的转换，其中可以指定任意数量的以下布尔关键字选项（除 `compose` 外，所有选项默认为 `false`）：

  * `compose=false`：不执行规范组合
  * `decompose=true`：执行规范分解而不是规范组合（如果存在，则忽略 `compose=true`）
  * `compat=true`：兼容等价物被规范化
  * `casefold=true`：执行 Unicode 大小写折叠，例如用于不区分大小写的字符串比较
  * `newline2lf=true`、`newline2ls=true` 或 `newline2ps=true`：将各种换行序列（LF、CRLF、CR、NEL）转换为换行符（LF）、行分隔符（LS）或段落分隔符（PS）字符
  * `stripmark=true`：去除变音符号（例如重音符）
  * `stripignore=true`：去除 Unicode 的“默认可忽略”字符（例如软连字符或从左到右标记）
  * `stripcc=true`：去除控制字符；水平制表符和换页符被转换为空格；换行符也被转换为空格，除非指定了换行转换标志
  * `rejectna=true`：如果发现未分配的代码点，则抛出错误
  * `stable=true`：强制 Unicode 版本稳定性（绝不引入早期 Unicode 版本中缺失的字符）

您还可以使用 `chartransform` 关键字（默认为 `identity`）传递一个任意的 *函数*，将 `Integer` 代码点映射到代码点，该函数在处理 `s` 中的每个字符时被调用，以执行任意额外的规范化。例如，通过传递 `chartransform=Unicode.julia_chartransform`，您可以应用一些 Julia 特定的字符规范化，这些规范化是在解析标识符时由 Julia 执行的（除了 NFC 规范化：`compose=true, stable=true`）。

例如，NFKC 对应于选项 `compose=true, compat=true, stable=true`。

# 示例

```jldoctest
julia> "é" == Unicode.normalize("é") #LHS: Unicode U+00e9, RHS: U+0065 & U+0301
true

julia> "μ" == Unicode.normalize("µ", compat=true) #LHS: Unicode U+03bc, RHS: Unicode U+00b5
true

julia> Unicode.normalize("JuLiA", casefold=true)
"julia"

julia> Unicode.normalize("JúLiA", stripmark=true)
"JuLiA"
```

!!! compat "Julia 1.8"
    `chartransform` 关键字参数需要 Julia 1.8。

