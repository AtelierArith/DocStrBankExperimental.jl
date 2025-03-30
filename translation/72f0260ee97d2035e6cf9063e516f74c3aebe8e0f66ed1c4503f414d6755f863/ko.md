```
vcat(A...)
```

배열이나 숫자를 수직으로 연결합니다. [`cat`](@ref)`(A...; dims=1)`와 같으며, 구문 `[a; b; c]`와도 같습니다.

큰 배열 벡터를 연결할 때, `reduce(vcat, A)`는 `A isa AbstractVector{<:AbstractVecOrMat}`일 때 효율적인 방법을 호출하며, 쌍으로 작업하는 대신에 사용됩니다.

또한 [`hcat`](@ref), [`Iterators.flatten`](@ref), [`stack`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> v = vcat([1,2], [3,4])
4-element Vector{Int64}:
 1
 2
 3
 4

julia> v == vcat(1, 2, [3,4])  # 숫자도 허용
true

julia> v == [1; 2; [3,4]]  # 동일한 작업을 위한 구문
true

julia> summary(ComplexF64[1; 2; [3,4]])  # 요소 유형을 제공하는 구문
"4-element Vector{ComplexF64}"

julia> vcat(range(1, 2, length=3))  # 지연 범위를 수집
3-element Vector{Float64}:
 1.0
 1.5
 2.0

julia> two = ([10, 20, 30]', Float64[4 5 6; 7 8 9])  # 행 벡터와 행렬
([10 20 30], [4.0 5.0 6.0; 7.0 8.0 9.0])

julia> vcat(two...)
3×3 Matrix{Float64}:
 10.0  20.0  30.0
  4.0   5.0   6.0
  7.0   8.0   9.0

julia> vs = [[1, 2], [3, 4], [5, 6]];

julia> reduce(vcat, vs)  # vcat(vs...)보다 더 효율적
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6

julia> ans == collect(Iterators.flatten(vs))
true
```
