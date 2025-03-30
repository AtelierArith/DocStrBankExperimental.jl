```
styled(content::AbstractString) -> AnnotatedString
```

构造一个样式化字符串。在字符串中，`{<specs>:<content>}` 结构根据以逗号分隔的规格 `<specs>` 列表对 `<content>` 应用格式。每个规格可以是字体名称、内联字体规格或 `key=value` 对。若值包含任何字符 `,=:{}`，则必须用 `{...}` 包裹。

这是 [`@styled_str`](@ref) 宏的功能等价物，只是没有插值功能。
