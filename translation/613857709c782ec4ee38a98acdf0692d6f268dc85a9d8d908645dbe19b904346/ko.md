```
permutedims(v::AbstractVector)
```

벡터 `v`를 `1 × length(v)` 행렬로 변형합니다. 이 작업은 [`transpose`](@ref)와 다르게 재귀적이지 않으며, 이는 비수치 값의 배열에 특히 유용합니다(재귀적 `transpose`는 오류를 발생시킬 수 있습니다).

# 예제

`transpose`와 달리, `permutedims`는 문자열과 같은 임의의 비수치 요소로 구성된 벡터에서 사용할 수 있습니다:

```jldoctest
julia> permutedims(["a", "b", "c"])
1×3 Matrix{String}:
 "a"  "b"  "c"
```

숫자로 구성된 벡터의 경우, `permutedims(v)`는 `transpose(v)`와 유사하게 작동하지만 반환 유형이 다릅니다(원래 배열 `v`와 메모리를 공유하지만, `LinearAlgebra.Transpose` 뷰 대신 [`reshape`](@ref)를 사용합니다):

```jldoctest; setup = :(using LinearAlgebra)
julia> v = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> p = permutedims(v)
1×4 Matrix{Int64}:
 1  2  3  4

julia> r = transpose(v)
1×4 transpose(::Vector{Int64}) with eltype Int64:
 1  2  3  4

julia> p == r
true

julia> typeof(r)
Transpose{Int64, Vector{Int64}}

julia> p[1] = 5; r[2] = 6; # p 또는 r을 변형하면 v도 변경됩니다.

julia> v # p와 r 모두와 메모리를 공유합니다.
4-element Vector{Int64}:
 5
 6
 3
 4
```

그러나 `permutedims`는 요소가 숫자 행렬인 벡터에 대해 `transpose`와 다른 결과를 생성합니다:

```jldoctest; setup = :(using LinearAlgebra)
julia> V = [[[1 2; 3 4]]; [[5 6; 7 8]]]
2-element Vector{Matrix{Int64}}:
 [1 2; 3 4]
 [5 6; 7 8]

julia> permutedims(V)
1×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]  [5 6; 7 8]

julia> transpose(V)
1×2 transpose(::Vector{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 3; 2 4]  [5 7; 6 8]
```
