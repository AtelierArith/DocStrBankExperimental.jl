```
cumprod(A; dims::Integer)
```

주어진 차원 `dim`에 따라 누적 곱을 계산합니다. 성능을 위해 미리 할당된 출력 배열을 사용하고 출력의 정밀도를 제어하기 위해 [`cumprod!`](@ref)도 참조하십시오 (예: 오버플로우를 피하기 위해).

# 예제

```jldoctest
julia> a = Int8[1 2 3; 4 5 6];

julia> cumprod(a, dims=1)
2×3 Matrix{Int64}:
 1   2   3
 4  10  18

julia> cumprod(a, dims=2)
2×3 Matrix{Int64}:
 1   2    6
 4  20  120
```
