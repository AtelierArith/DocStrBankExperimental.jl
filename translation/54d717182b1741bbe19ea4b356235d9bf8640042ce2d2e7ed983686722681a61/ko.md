```
hcat(A...)
```

배열이나 숫자를 수평으로 연결합니다. [`cat`](@ref)`(A...; dims=2)`와 같으며, 구문 `[a b c]` 또는 `[a;; b;; c]`와도 같습니다.

큰 배열 벡터의 경우, `reduce(hcat, A)`는 `A isa AbstractVector{<:AbstractVecOrMat}`일 때 효율적인 방법을 호출합니다. 벡터의 벡터의 경우, 이것은 [`stack`](@ref)`(A)`로도 작성할 수 있습니다.

또한 [`vcat`](@ref), [`hvcat`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> hcat([1,2], [3,4], [5,6])
2×3 Matrix{Int64}:
 1  3  5
 2  4  6

julia> hcat(1, 2, [30 40], [5, 6, 7]')  # 숫자도 허용
1×7 Matrix{Int64}:
 1  2  30  40  5  6  7

julia> ans == [1 2 [30 40] [5, 6, 7]']  # 동일한 작업을 위한 구문
true

julia> Float32[1 2 [30 40] [5, 6, 7]']  # eltype을 제공하는 구문
1×7 Matrix{Float32}:
 1.0  2.0  30.0  40.0  5.0  6.0  7.0

julia> ms = [zeros(2,2), [1 2; 3 4], [50 60; 70 80]];

julia> reduce(hcat, ms)  # hcat(ms...)보다 더 효율적
2×6 Matrix{Float64}:
 0.0  0.0  1.0  2.0  50.0  60.0
 0.0  0.0  3.0  4.0  70.0  80.0

julia> stack(ms) |> summary  # 행렬 벡터에 대해 불일치
"2×2×3 Array{Float64, 3}"

julia> hcat(Int[], Int[], Int[])  # 크기 (0,)인 빈 벡터
0×3 Matrix{Int64}

julia> hcat([1.1, 9.9], Matrix(undef, 2, 0))  # 빈 2×0 행렬과 함께 hcat
2×1 Matrix{Any}:
 1.1
 9.9
```
