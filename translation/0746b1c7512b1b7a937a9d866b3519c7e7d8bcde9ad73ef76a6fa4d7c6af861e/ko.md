```
A'
adjoint(A)
```

게으른 수반(켤레 전치). `adjoint`는 요소에 재귀적으로 적용된다는 점에 유의하십시오.

숫자 유형의 경우, `adjoint`는 복소수 켤레를 반환하며, 따라서 실수에 대해서는 항등 함수와 동일합니다.

이 작업은 선형 대수 사용을 위해 의도되었습니다 - 일반 데이터 조작에 대해서는 [`permutedims`](@ref Base.permutedims)를 참조하십시오.

# 예제

```jldoctest
julia> A = [3+2im 9+2im; 0  0]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 0+0im  0+0im

julia> B = A' # equivalently adjoint(A)
2×2 adjoint(::Matrix{Complex{Int64}}) with eltype Complex{Int64}:
 3-2im  0+0im
 9-2im  0+0im

julia> B isa Adjoint
true

julia> adjoint(B) === A # 수반의 수반은 부모를 풀어냅니다
true

julia> Adjoint(B) # 그러나 생성자는 항상 인수를 래핑합니다
2×2 adjoint(adjoint(::Matrix{Complex{Int64}})) with eltype Complex{Int64}:
 3+2im  9+2im
 0+0im  0+0im

julia> B[1,2] = 4 + 5im; # B를 수정하면 A도 자동으로 수정됩니다

julia> A
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 4-5im  0+0im
```

실수 행렬의 경우, `adjoint` 작업은 `transpose`와 동일합니다.

```jldoctest
julia> A = reshape([x for x in 1:4], 2, 2)
2×2 Matrix{Int64}:
 1  3
 2  4

julia> A'
2×2 adjoint(::Matrix{Int64}) with eltype Int64:
 1  2
 3  4

julia> adjoint(A) == transpose(A)
true
```

`AbstractVector`의 수반은 행 벡터입니다:

```jldoctest
julia> x = [3, 4im]
2-element Vector{Complex{Int64}}:
 3 + 0im
 0 + 4im

julia> x'
1×2 adjoint(::Vector{Complex{Int64}}) with eltype Complex{Int64}:
 3+0im  0-4im

julia> x'x # 내적을 계산합니다, 동등하게 x' * x
25 + 0im
```

행렬의 행렬에 대해 개별 블록은 재귀적으로 작동합니다:

```jldoctest
julia> A = reshape([x + im*x for x in 1:4], 2, 2)
2×2 Matrix{Complex{Int64}}:
 1+1im  3+3im
 2+2im  4+4im

julia> C = reshape([A, 2A, 3A, 4A], 2, 2)
2×2 Matrix{Matrix{Complex{Int64}}}:
 [1+1im 3+3im; 2+2im 4+4im]  [3+3im 9+9im; 6+6im 12+12im]
 [2+2im 6+6im; 4+4im 8+8im]  [4+4im 12+12im; 8+8im 16+16im]

julia> C'
2×2 adjoint(::Matrix{Matrix{Complex{Int64}}}) with eltype Adjoint{Complex{Int64}, Matrix{Complex{Int64}}}:
 [1-1im 2-2im; 3-3im 4-4im]    [2-2im 4-4im; 6-6im 8-8im]
 [3-3im 6-6im; 9-9im 12-12im]  [4-4im 8-8im; 12-12im 16-16im]
```
