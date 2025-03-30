```
maximum!(r, A)
```

`A`의 단일 차원에서 최대 값을 계산하고 결과를 `r`에 기록합니다.

!!! 경고     변형된 인수가 다른 인수와 메모리를 공유할 때 동작이 예기치 않게 될 수 있습니다.

# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> maximum!([1; 1], A)
2-element Vector{Int64}:
 2
 4

julia> maximum!([1 1], A)
1×2 Matrix{Int64}:
 3  4
```
