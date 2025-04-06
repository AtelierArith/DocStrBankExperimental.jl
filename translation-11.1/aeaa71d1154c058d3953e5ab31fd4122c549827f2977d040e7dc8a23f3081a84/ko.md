```
rmul!(A, B)
```

행렬-행렬 곱 $AB$를 계산하여 `A`를 덮어쓰고 결과를 반환합니다. 여기서 `B`는 [`Diagonal`](@ref), [`UpperTriangular`](@ref) 또는 [`LowerTriangular`](@ref)와 같은 특수 행렬 유형이거나, [`QR`](@ref)와 같은 일부 직교 유형이어야 합니다.

# 예제

```jldoctest
julia> A = [0 1; 1 0];

julia> B = UpperTriangular([1 2; 0 3]);

julia> rmul!(A, B);

julia> A
2×2 Matrix{Int64}:
 0  3
 1  2

julia> A = [1.0 2.0; 3.0 4.0];

julia> F = qr([0 1; -1 0]);

julia> rmul!(A, F.Q)
2×2 Matrix{Float64}:
 2.0  1.0
 4.0  3.0
```
