```
map(f, A::AbstractArray...) -> N-array
```

동일한 [`ndims`](@ref)를 가진 다차원 배열에 작용할 때, 모든 배열은 동일한 [`axes`](@ref)를 가져야 하며, 결과도 마찬가지입니다.

불일치하는 크기를 허용하는 [`broadcast`](@ref)도 참고하세요.

# 예제

```
julia> map(//, [1 2; 3 4], [4 3; 2 1])
2×2 Matrix{Rational{Int64}}:
 1//4  2//3
 3//2  4//1

julia> map(+, [1 2; 3 4], zeros(2,1))
ERROR: DimensionMismatch

julia> map(+, [1 2; 3 4], [1,10,100,1000], zeros(3,1))  # 3번째가 소진될 때까지 반복
3-element Vector{Float64}:
   2.0
  13.0
 102.0
```
