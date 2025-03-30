```
axpy!(α, x::AbstractArray, y::AbstractArray)
```

`y`를 `x * α + y`로 덮어쓰고 `y`를 반환합니다. `x`와 `y`가 동일한 축을 가지면, 이는 `y .+= x .* a`와 동등합니다.

# 예제

```jldoctest
julia> x = [1; 2; 3];

julia> y = [4; 5; 6];

julia> axpy!(2, x, y)
3-element Vector{Int64}:
  6
  9
 12
```
