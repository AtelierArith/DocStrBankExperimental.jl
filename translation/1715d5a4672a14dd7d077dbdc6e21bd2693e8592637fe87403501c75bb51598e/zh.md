```
Date(d::AbstractString, format::AbstractString; locale="english") -> Date
```

通过解析 `d` 日期字符串并遵循 `format` 字符串中给定的模式来构造 `Date`（有关语法，请参见 [`DateFormat`](@ref)）。

!!! note
    此方法每次调用时都会创建一个 `DateFormat` 对象。建议您先创建一个 [`DateFormat`](@ref) 对象，并将其作为第二个参数使用，以避免在重复使用相同格式时造成性能损失。


# 示例

```jldoctest
julia> Date("2020-01-01", "yyyy-mm-dd")
2020-01-01

julia> a = ("2020-01-01", "2020-01-02");

julia> [Date(d, dateformat"yyyy-mm-dd") for d ∈ a] # preferred
2-element Vector{Date}:
 2020-01-01
 2020-01-02
```
