```
Time(t::AbstractString, format::AbstractString; locale="english") -> Time
```

通过解析 `t` 时间字符串并遵循 `format` 字符串中给定的模式来构造 `Time`（有关语法，请参见 [`DateFormat`](@ref)）。

!!! note
    此方法每次调用时都会创建一个 `DateFormat` 对象。建议您先创建一个 [`DateFormat`](@ref) 对象，并将其作为第二个参数使用，以避免在重复使用相同格式时造成性能损失。


# 示例

```jldoctest
julia> Time("12:34pm", "HH:MMp")
12:34:00

julia> a = ("12:34pm", "2:34am");

julia> [Time(d, dateformat"HH:MMp") for d ∈ a] # preferred
2-element Vector{Time}:
 12:34:00
 02:34:00
```
