```
axpby!(α, x::AbstractArray, β, y::AbstractArray)
```

`y`를 `x * α + y * β`로 덮어쓰고 `y`를 반환합니다. `x`와 `y`가 동일한 축을 가지면, `y .= x .* a .+ y .* β`와 동일합니다.

# 예제

```jldoctest
julia> x = [1; 2; 3];

julia> y = [4; 5; 6];

julia> axpby!(2, x, 2, y)
3-element Vector{Int64}:
 10
 14
 18
```
