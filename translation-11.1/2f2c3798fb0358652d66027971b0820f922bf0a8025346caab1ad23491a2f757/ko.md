```
maximum(A::AbstractArray; dims)
```

주어진 차원에서 배열의 최대값을 계산합니다. 두 개 이상의 인수의 최대값을 취하는 [`max(a,b)`](@ref) 함수도 참조하십시오. 이 함수는 `max.(a,b)`를 통해 배열에 요소별로 적용할 수 있습니다.

또한 다음을 참조하십시오: [`maximum!`](@ref), [`extrema`](@ref), [`findmax`](@ref), [`argmax`](@ref).

# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> maximum(A, dims=1)
1×2 Matrix{Int64}:
 3  4

julia> maximum(A, dims=2)
2×1 Matrix{Int64}:
 2
 4
```
