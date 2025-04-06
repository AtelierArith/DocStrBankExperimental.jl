```
repeat(A::AbstractArray, counts::Integer...)
```

주어진 차원에서 배열 `A`를 지정된 수만큼 반복하여 배열을 생성합니다. 반복 횟수는 `counts`로 지정됩니다.

참고: [`fill`](@ref), [`Iterators.repeated`](@ref), [`Iterators.cycle`](@ref).

# 예제

```jldoctest
julia> repeat([1, 2, 3], 2)
6-element Vector{Int64}:
 1
 2
 3
 1
 2
 3

julia> repeat([1, 2, 3], 2, 3)
6×3 Matrix{Int64}:
 1  1  1
 2  2  2
 3  3  3
 1  1  1
 2  2  2
 3  3  3
```
