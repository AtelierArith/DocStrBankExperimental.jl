```
\(x, y)
```

왼쪽 나눗셈 연산자: `x`의 역수에 `y`를 왼쪽에서 곱하는 것입니다. 정수 인수에 대해 부동 소수점 결과를 제공합니다.

# 예제

```jldoctest
julia> 3 \ 6
2.0

julia> inv(3) * 6
2.0

julia> A = [4 3; 2 1]; x = [5, 6];

julia> A \ x
2-element Vector{Float64}:
  6.5
 -7.0

julia> inv(A) * x
2-element Vector{Float64}:
  6.5
 -7.0
```
