```
combine_styles(cs...) -> BroadcastStyle
```

决定对于任意数量的值参数使用哪种 `BroadcastStyle`。使用 [`BroadcastStyle`](@ref) 获取每个参数的样式，并使用 [`result_style`](@ref) 组合样式。

# 示例

```jldoctest
julia> Broadcast.combine_styles([1], [1 2; 3 4])
Base.Broadcast.DefaultArrayStyle{2}()
```
