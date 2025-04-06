```
minimum!(r, A)
```

`A`의 단일 차원에서 최소값을 계산하고 결과를 `r`에 기록합니다.

!!! 경고     변형된 인수가 다른 인수와 메모리를 공유할 경우 예상치 못한 동작이 발생할 수 있습니다.

# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> minimum!([1; 1], A)
2-element Vector{Int64}:
 1
 3

julia> minimum!([1 1], A)
1×2 Matrix{Int64}:
 1  2
```
