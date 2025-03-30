```
permutedims(A::AbstractArray, perm)
permutedims(A::AbstractMatrix)
```

배열 `A`의 차원(축)을 변경합니다. `perm`은 변경을 지정하는 `ndims(A)` 정수의 튜플 또는 벡터입니다.

`A`가 2차원 배열([`AbstractMatrix`](@ref))인 경우, `perm`은 기본적으로 `(2,1)`으로 설정되어 `A`의 두 축(행과 열)을 교환합니다. 이는 [`transpose`](@ref)와 다르며, 이 연산은 재귀적이지 않기 때문에 비수치 값(재귀적 `transpose`가 오류를 발생시키는 경우) 및 선형 연산자를 나타내지 않는 2차원 배열에 특히 유용합니다.

1차원 배열의 경우 [`permutedims(v::AbstractVector)`](@ref)를 참조하십시오. 이는 1행 “행렬”을 반환합니다.

또한 [`permutedims!`](@ref), [`PermutedDimsArray`](@ref), [`transpose`](@ref), [`invperm`](@ref)를 참조하십시오.

# 예제

## 2차원 배열:

`transpose`와 달리 `permutedims`는 문자열과 같은 임의의 비수치 요소로 구성된 2차원 배열의 행과 열을 교환하는 데 사용할 수 있습니다:

```jldoctest
julia> A = ["a" "b" "c"
            "d" "e" "f"]
2×3 Matrix{String}:
 "a"  "b"  "c"
 "d"  "e"  "f"

julia> permutedims(A)
3×2 Matrix{String}:
 "a"  "d"
 "b"  "e"
 "c"  "f"
```

그리고 `permutedims`는 요소가 자체적으로 수치 행렬인 행렬에 대해 `transpose`와 다른 결과를 생성합니다:

```jldoctest; setup = :(using LinearAlgebra)
julia> a = [1 2; 3 4];

julia> b = [5 6; 7 8];

julia> c = [9 10; 11 12];

julia> d = [13 14; 15 16];

julia> X = [[a] [b]; [c] [d]]
2×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]     [5 6; 7 8]
 [9 10; 11 12]  [13 14; 15 16]

julia> permutedims(X)
2×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]  [9 10; 11 12]
 [5 6; 7 8]  [13 14; 15 16]

julia> transpose(X)
2×2 transpose(::Matrix{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 3; 2 4]  [9 11; 10 12]
 [5 7; 6 8]  [13 15; 14 16]
```

## 다차원 배열

```jldoctest
julia> A = reshape(Vector(1:8), (2,2,2))
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 5  7
 6  8

julia> perm = (3, 1, 2); # 마지막 차원을 첫 번째로 이동

julia> B = permutedims(A, perm)
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 5  6

[:, :, 2] =
 3  4
 7  8

julia> A == permutedims(B, invperm(perm)) # 역변환
true
```

`B = permutedims(A, perm)`의 각 차원 `i`에 대해, `A`의 해당 차원은 `perm[i]`가 됩니다. 이는 `size(B, i) == size(A, perm[i])`가 성립함을 의미합니다.

```jldoctest
julia> A = randn(5, 7, 11, 13);

julia> perm = [4, 1, 3, 2];

julia> B = permutedims(A, perm);

julia> size(B)
(13, 5, 11, 7)

julia> size(A)[perm] == ans
true
```
