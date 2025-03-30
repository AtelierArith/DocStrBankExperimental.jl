```
zero(x)
zero(::Type)
```

`x`의 타입에 대한 덧셈 항등원 요소를 가져옵니다 (`x`는 타입 자체를 지정할 수도 있습니다).

또한 [`iszero`](@ref), [`one`](@ref), [`oneunit`](@ref), [`oftype`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> zero(1)
0

julia> zero(big"2.0")
0.0

julia> zero(rand(2,2))
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0
```
