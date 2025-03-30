```
lmul!(A, B)
```

행렬-행렬 곱 $AB$를 계산하고 `B`를 덮어쓰며 결과를 반환합니다. 여기서 `A`는 [`Diagonal`](@ref), [`UpperTriangular`](@ref) 또는 [`LowerTriangular`](@ref)와 같은 특수 행렬 유형이거나, [`QR`](@ref)에서 볼 수 있는 일부 직교 유형이어야 합니다.

# 예제

```jldoctest
julia> B = [0 1; 1 0];

julia> A = UpperTriangular([1 2; 0 3]);

julia> lmul!(A, B);

julia> B
2×2 Matrix{Int64}:
 2  1
 3  0

julia> B = [1.0 2.0; 3.0 4.0];

julia> F = qr([0 1; -1 0]);

julia> lmul!(F.Q, B)
2×2 Matrix{Float64}:
 3.0  4.0
 1.0  2.0
```
