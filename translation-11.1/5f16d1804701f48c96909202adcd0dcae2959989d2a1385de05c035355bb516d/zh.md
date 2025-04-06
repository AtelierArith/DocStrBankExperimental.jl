```
DateTime(dt::AbstractString, format::AbstractString; locale="english") -> DateTime
```

通过解析遵循 `format` 字符串中给定模式的 `dt` 日期时间字符串来构造 `DateTime`（有关语法，请参见 [`DateFormat`](@ref)）。

!!! note
    此方法每次调用时都会创建一个 `DateFormat` 对象。建议您先创建一个 [`DateFormat`](@ref) 对象，并将其作为第二个参数使用，以避免在重复使用相同格式时造成性能损失。


# 示例

```jldoctest
julia> DateTime("2020-01-01", "yyyy-mm-dd")
2020-01-01T00:00:00

julia> a = ("2020-01-01", "2020-01-02");

julia> [DateTime(d, dateformat"yyyy-mm-dd") for d ∈ a] # preferred
2-element Vector{DateTime}:
 2020-01-01T00:00:00
 2020-01-02T00:00:00
```
