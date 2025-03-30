```
transpose(A)
```

지연 전치. 반환된 객체를 변형하면 `A`도 적절하게 변형됩니다. 종종, 그러나 항상 그런 것은 아니며, `Transpose(A)`를 생성합니다. 여기서 `Transpose`는 지연 전치 래퍼입니다. 이 작업은 재귀적이라는 점에 유의하십시오.

이 작업은 선형 대수 사용을 위해 의도되었습니다 - 일반 데이터 조작에 대해서는 [`permutedims`](@ref Base.permutedims)를 참조하십시오. 이는 비재귀적입니다.

# 예제

```jldoctest
julia> A = [3 2; 0 0]
2×2 Matrix{Int64}:
 3  2
 0  0

julia> B = transpose(A)
2×2 transpose(::Matrix{Int64}) with eltype Int64:
 3  0
 2  0

julia> B isa Transpose
true

julia> transpose(B) === A # 전치의 전치는 부모를 풀어냅니다
true

julia> Transpose(B) # 그러나 생성자는 항상 인수를 래핑합니다
2×2 transpose(transpose(::Matrix{Int64})) with eltype Int64:
 3  2
 0  0

julia> B[1,2] = 4; # B를 수정하면 A도 자동으로 수정됩니다

julia> A
2×2 Matrix{Int64}:
 3  2
 4  0
```

복소 행렬의 경우, `adjoint` 연산은 켤레 전치와 동등합니다.

```jldoctest
julia> A = reshape([Complex(x, x) for x in 1:4], 2, 2)
2×2 Matrix{Complex{Int64}}:
 1+1im  3+3im
 2+2im  4+4im

julia> adjoint(A) == conj(transpose(A))
true
```

`AbstractVector`의 `transpose`는 행 벡터입니다:

```jldoctest
julia> v = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> transpose(v) # 행 벡터를 반환합니다
1×3 transpose(::Vector{Int64}) with eltype Int64:
 1  2  3

julia> transpose(v) * v # 내적을 계산합니다
14
```

행렬의 행렬에 대해 개별 블록은 재귀적으로 작동합니다:

```jldoctest
julia> C = [1 3; 2 4]
2×2 Matrix{Int64}:
 1  3
 2  4

julia> D = reshape([C, 2C, 3C, 4C], 2, 2) # 블록 행렬을 구성합니다
2×2 Matrix{Matrix{Int64}}:
 [1 3; 2 4]  [3 9; 6 12]
 [2 6; 4 8]  [4 12; 8 16]

julia> transpose(D) # 블록이 재귀적으로 전치됩니다
2×2 transpose(::Matrix{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 2; 3 4]   [2 4; 6 8]
 [3 6; 9 12]  [4 8; 12 16]
```
