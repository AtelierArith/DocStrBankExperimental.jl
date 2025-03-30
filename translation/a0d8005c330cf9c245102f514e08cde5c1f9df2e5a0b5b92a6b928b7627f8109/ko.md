```
<:(T1, T2)
```

서브타입 연산자: `T1` 유형의 모든 값이 `T2` 유형이기도 할 경우에만 `true`를 반환합니다.

# 예시

```jldoctest
julia> Float64 <: AbstractFloat
true

julia> Vector{Int} <: AbstractArray
true

julia> Matrix{Float64} <: Matrix{AbstractFloat}
false
```
