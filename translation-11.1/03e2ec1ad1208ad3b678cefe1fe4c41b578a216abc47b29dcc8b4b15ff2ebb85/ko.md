```
!==(x, y)
≢(x,y)
```

항상 [`===`](@ref)와 반대의 답변을 제공합니다.

# 예시

```jldoctest
julia> a = [1, 2]; b = [1, 2];

julia> a ≢ b
true

julia> a ≢ a
false
```
