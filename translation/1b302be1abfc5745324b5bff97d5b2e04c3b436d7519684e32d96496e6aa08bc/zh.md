```
tryparse(::Type{SimpleColor}, rgb::String)
```

尝试将 `rgb` 解析为 `SimpleColor`。如果 `rgb` 以 `#` 开头并且长度为 7，则将其转换为以 `RGBTuple` 为基础的 `SimpleColor`。如果 `rgb` 以 `a`-`z` 开头，则将 `rgb` 解释为颜色名称并转换为以 `Symbol` 为基础的 `SimpleColor`。

否则，返回 `nothing`。

# 示例

```jldoctest; setup = :(import StyledStrings.SimpleColor)
julia> tryparse(SimpleColor, "blue")
SimpleColor(blue)

julia> tryparse(SimpleColor, "#9558b2")
SimpleColor(#9558b2)

julia> tryparse(SimpleColor, "#nocolor")
```
