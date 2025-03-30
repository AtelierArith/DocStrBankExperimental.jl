```
lazy"str"
```

使用常规字符串插值语法创建一个 [`LazyString`](@ref)。请注意，插值在 LazyString 构造时被 *评估*，但 *打印* 被延迟到第一次访问字符串时。

有关并发程序的安全属性，请参见 [`LazyString`](@ref) 文档。

# 示例

```
julia> n = 5; str = lazy"n is $n"
"n is 5"

julia> typeof(str)
LazyString
```

!!! compat "Julia 1.8"
    `lazy"str"` 需要 Julia 1.8 或更高版本。

