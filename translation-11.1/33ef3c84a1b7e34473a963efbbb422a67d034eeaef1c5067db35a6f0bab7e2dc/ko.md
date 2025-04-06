```
cat(A...; dims)
```

입력 배열을 `dims`에 지정된 차원에 따라 연결합니다.

차원 `d in dims`에 따라 출력 배열의 크기는 `sum(size(a,d) for a in A)`입니다. 다른 차원에서는 모든 입력 배열이 동일한 크기를 가져야 하며, 이는 해당 차원에서 출력 배열의 크기도 됩니다.

`dims`가 단일 숫자인 경우, 서로 다른 배열이 해당 차원에 따라 밀집되어 있습니다. `dims`가 여러 차원을 포함하는 iterable인 경우, 이러한 차원에 따라 위치가 각 입력 배열에 대해 동시에 증가하며, 다른 곳은 0으로 채워집니다. 이를 통해 `cat(matrices...; dims=(1,2))`와 같이 블록 대각 행렬을 구성할 수 있으며, 그 고차원 유사체도 가능합니다.

특수한 경우 `dims=1`은 [`vcat`](@ref)이고, `dims=2`는 [`hcat`](@ref)입니다. 또한 [`hvcat`](@ref), [`hvncat`](@ref), [`stack`](@ref), [`repeat`](@ref)도 참조하십시오.

키워드는 `Val(dims)`도 허용합니다.

!!! compat "Julia 1.8"
    여러 차원에 대해 `dims = Val(::Tuple)`이 Julia 1.8에 추가되었습니다.


# 예제

서로 다른 차원에서 두 배열을 연결합니다:

```jldoctest
julia> a = [1 2 3]
1×3 Matrix{Int64}:
 1  2  3

julia> b = [4 5 6]
1×3 Matrix{Int64}:
 4  5  6

julia> cat(a, b; dims=1)
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> cat(a, b; dims=2)
1×6 Matrix{Int64}:
 1  2  3  4  5  6

julia> cat(a, b; dims=(1, 2))
2×6 Matrix{Int64}:
 1  2  3  0  0  0
 0  0  0  4  5  6
```

# 확장 도움말

3D 배열을 연결합니다:

```jldoctest
julia> a = ones(2, 2, 3);

julia> b = ones(2, 2, 4);

julia> c = cat(a, b; dims=3);

julia> size(c) == (2, 2, 7)
true
```

서로 다른 크기의 배열을 연결합니다:

```jldoctest
julia> cat([1 2; 3 4], [pi, pi], fill(10, 2,3,1); dims=2)  # hcat과 동일
2×6×1 Array{Float64, 3}:
[:, :, 1] =
 1.0  2.0  3.14159  10.0  10.0  10.0
 3.0  4.0  3.14159  10.0  10.0  10.0
```

블록 대각 행렬을 구성합니다:

```
julia> cat(true, trues(2,2), trues(4)', dims=(1,2))  # 블록 대각
4×7 Matrix{Bool}:
 1  0  0  0  0  0  0
 0  1  1  0  0  0  0
 0  1  1  0  0  0  0
 0  0  0  1  1  1  1
```

```
julia> cat(1, [2], [3;;]; dims=Val(2))
1×3 Matrix{Int64}:
 1  2  3
```

!!! note
    `cat`는 두 문자열을 결합하지 않으며, `*`를 사용해야 할 수 있습니다.


```jldoctest
julia> a = "aaa";

julia> b = "bbb";

julia> cat(a, b; dims=1)
2-element Vector{String}:
 "aaa"
 "bbb"

julia> cat(a, b; dims=2)
1×2 Matrix{String}:
 "aaa"  "bbb"

julia> a * b
"aaabbb"
```
