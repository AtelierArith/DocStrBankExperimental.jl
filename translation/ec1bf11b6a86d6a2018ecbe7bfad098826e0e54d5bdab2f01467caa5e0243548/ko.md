```
combine_styles(cs...) -> BroadcastStyle
```

값 인수의 수에 따라 사용할 `BroadcastStyle`을 결정합니다. 각 인수에 대한 스타일을 얻기 위해 [`BroadcastStyle`](@ref)를 사용하고, 스타일을 결합하기 위해 [`result_style`](@ref)를 사용합니다.

# 예제

```jldoctest
julia> Broadcast.combine_styles([1], [1 2; 3 4])
Base.Broadcast.DefaultArrayStyle{2}()
```
