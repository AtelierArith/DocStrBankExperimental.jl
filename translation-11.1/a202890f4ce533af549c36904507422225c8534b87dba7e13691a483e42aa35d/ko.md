```
accumulate!(op, B, A; [dims], [init])
```

누적 연산 `op`를 `A`의 차원 `dims`를 따라 수행하고 결과를 `B`에 저장합니다. 벡터의 경우 `dims`를 제공하는 것은 선택 사항입니다. 키워드 인수 `init`이 주어지면, 그 값이 누적을 초기화하는 데 사용됩니다.

!!! 경고     변형된 인수가 다른 인수와 메모리를 공유할 경우 동작이 예기치 않게 될 수 있습니다.

자세한 내용은 [`accumulate`](@ref), [`cumsum!`](@ref), [`cumprod!`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> x = [1, 0, 2, 0, 3];

julia> y = rand(5);

julia> accumulate!(+, y, x);

julia> y
5-element Vector{Float64}:
 1.0
 1.0
 3.0
 3.0
 6.0

julia> A = [1 2 3; 4 5 6];

julia> B = similar(A);

julia> accumulate!(-, B, A, dims=1)
2×3 Matrix{Int64}:
  1   2   3
 -3  -3  -3

julia> accumulate!(*, B, A, dims=2, init=10)
2×3 Matrix{Int64}:
 10   20    60
 40  200  1200
```
