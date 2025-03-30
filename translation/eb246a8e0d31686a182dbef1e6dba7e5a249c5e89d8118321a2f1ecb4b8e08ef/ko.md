```
minimum(A::AbstractArray; dims)
```

주어진 차원에 대해 배열의 최소값을 계산합니다. 두 개 이상의 인수 중 최소값을 취하는 [`min(a,b)`](@ref) 함수도 참조하십시오. 이 함수는 `min.(a,b)`를 통해 배열에 요소별로 적용할 수 있습니다.

또한 다음을 참조하십시오: [`minimum!`](@ref), [`extrema`](@ref), [`findmin`](@ref), [`argmin`](@ref).

# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> minimum(A, dims=1)
1×2 Matrix{Int64}:
 1  2

julia> minimum(A, dims=2)
2×1 Matrix{Int64}:
 1
 3
```
