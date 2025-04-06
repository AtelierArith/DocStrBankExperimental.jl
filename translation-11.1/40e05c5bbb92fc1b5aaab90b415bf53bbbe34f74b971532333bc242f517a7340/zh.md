```
annotatedstring(values...)
```

使用它们的 [`print`](@ref) 表示从任意数量的 `values` 创建一个 `AnnotatedString`。

这类似于 [`string`](@ref)，但会处理以 [`AnnotatedString`](@ref) 或 [`AnnotatedChar`](@ref) 值的形式存在的任何注释。

另请参见 [`AnnotatedString`](@ref) 和 [`AnnotatedChar`](@ref)。

## 示例

```julia-repl
julia> annotatedstring("now a AnnotatedString")
"now a AnnotatedString"

julia> annotatedstring(AnnotatedString("annotated", [(1:9, :label => 1)]), ", and unannotated")
"annotated, and unannotated"
```
