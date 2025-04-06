```
stack(iter; [dims])
```

동일한 크기의 배열(또는 기타 반복 가능한 객체) 모음을 하나의 더 큰 배열로 결합하여 하나 이상의 새로운 차원에 따라 배열합니다.

기본적으로 요소의 축이 먼저 배치되어 `size(result) = (size(first(iter))..., size(iter)...)`가 됩니다. 이는 [`Iterators.flatten`](@ref)`(iter)`와 동일한 요소 순서를 가집니다.

키워드 `dims::Integer`를 사용하면, 대신 `iter`의 `i`번째 요소가 슬라이스 [`selectdim`](@ref)`(result, dims, i)`가 되어 `size(result, dims) == length(iter)`가 됩니다. 이 경우 `stack`은 동일한 `dims`로 [`eachslice`](@ref)의 동작을 반전시킵니다.

여러 가지 [`cat`](@ref) 함수도 배열을 결합합니다. 그러나 이들은 모두 배열의 기존(아마도 사소한) 차원을 확장하는 반면, 배열을 새로운 차원에 배치합니다. 또한 배열을 단일 컬렉션이 아닌 개별 인수로 허용합니다.

!!! compat "Julia 1.9"
    이 함수는 최소한 Julia 1.9가 필요합니다.


# 예제

```jldoctest
julia> vecs = (1:2, [30, 40], Float32[500, 600]);

julia> mat = stack(vecs)
2×3 Matrix{Float32}:
 1.0  30.0  500.0
 2.0  40.0  600.0

julia> mat == hcat(vecs...) == reduce(hcat, collect(vecs))
true

julia> vec(mat) == vcat(vecs...) == reduce(vcat, collect(vecs))
true

julia> stack(zip(1:4, 10:99))  # 반복 가능한 반복자의 모든 인스턴스를 허용
2×4 Matrix{Int64}:
  1   2   3   4
 10  11  12  13

julia> vec(ans) == collect(Iterators.flatten(zip(1:4, 10:99)))
true

julia> stack(vecs; dims=1)  # 모든 cat 함수와 달리, vecs[1]의 1차 축은 결과의 2차 축
3×2 Matrix{Float32}:
   1.0    2.0
  30.0   40.0
 500.0  600.0

julia> x = rand(3,4);

julia> x == stack(eachcol(x)) == stack(eachrow(x), dims=1)  # eachslice의 역
true
```

고차원 예제:

```jldoctest
julia> A = rand(5, 7, 11);

julia> E = eachslice(A, dims=2);  # 행렬의 벡터

julia> (element = size(first(E)), container = size(E))
(element = (5, 11), container = (7,))

julia> stack(E) |> size
(5, 11, 7)

julia> stack(E) == stack(E; dims=3) == cat(E...; dims=3)
true

julia> A == stack(E; dims=2)
true

julia> M = (fill(10i+j, 2, 3) for i in 1:5, j in 1:7);

julia> (element = size(first(M)), container = size(M))
(element = (2, 3), container = (5, 7))

julia> stack(M) |> size  # 모든 차원을 유지
(2, 3, 5, 7)

julia> stack(M; dims=1) |> size  # dims=1에 따라 vec(container)
(35, 2, 3)

julia> hvcat(5, M...) |> size  # hvcat은 행렬을 나란히 배치
(14, 15)
```
