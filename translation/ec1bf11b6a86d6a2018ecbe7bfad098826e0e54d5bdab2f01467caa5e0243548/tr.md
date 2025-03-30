```
combine_styles(cs...) -> BroadcastStyle
```

Herhangi bir değer argümanı için hangi `BroadcastStyle`'ın kullanılacağına karar verir. Her argüman için stil almak üzere [`BroadcastStyle`](@ref) kullanır ve stilleri birleştirmek için [`result_style`](@ref) kullanır.

# Örnekler

```jldoctest
julia> Broadcast.combine_styles([1], [1 2; 3 4])
Base.Broadcast.DefaultArrayStyle{2}()
```
