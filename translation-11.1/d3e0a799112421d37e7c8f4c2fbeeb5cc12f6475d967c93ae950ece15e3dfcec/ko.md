```
diff(A::AbstractVector)
diff(A::AbstractArray; dims::Integer)
```

벡터 또는 다차원 배열 `A`에 대한 유한 차분 연산자입니다. 후자의 경우, 작동할 차원을 `dims` 키워드 인수로 지정해야 합니다.

!!! compat "Julia 1.1"
    차원이 2보다 큰 배열에 대한 `diff`는 최소한 Julia 1.1이 필요합니다.


# 예제

```jldoctest
julia> a = [2 4; 6 16]
2×2 Matrix{Int64}:
 2   4
 6  16

julia> diff(a, dims=2)
2×1 Matrix{Int64}:
  2
 10

julia> diff(vec(a))
3-element Vector{Int64}:
  4
 -2
 12
```
