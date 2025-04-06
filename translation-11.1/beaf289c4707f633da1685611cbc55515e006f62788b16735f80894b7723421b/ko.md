```
imag(A::AbstractArray)
```

배열 `A`의 각 항목의 허수 부분을 포함하는 배열을 반환합니다.

`imag.(A)`와 동등하지만, `A`가 0차원일 경우 스칼라 대신 0차원 배열이 반환됩니다.

# 예제

```jldoctest
julia> imag([1, 2im, 3 + 4im])
3-element Vector{Int64}:
 0
 2
 4

julia> imag(fill(2 - im))
0-dimensional Array{Int64, 0}:
-1
```
