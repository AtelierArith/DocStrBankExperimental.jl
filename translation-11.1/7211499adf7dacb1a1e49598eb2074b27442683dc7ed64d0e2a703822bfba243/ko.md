```
clamp(x, T)::T
```

`x`를 `typemin(T)`와 `typemax(T)` 사이로 제한하고 결과를 타입 `T`로 변환합니다.

자세한 내용은 [`trunc`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> clamp(200, Int8)
127

julia> clamp(-200, Int8)
-128

julia> trunc(Int, 4pi^2)
39
```
