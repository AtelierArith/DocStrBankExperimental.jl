```
all!(r, A)
```

`A`의 단일 차원에 있는 모든 값이 `true`인지 테스트하고 결과를 `r`에 기록합니다.

!!! 경고     변형된 인수가 다른 인수와 메모리를 공유할 경우 동작이 예기치 않게 될 수 있습니다.

# 예제

```jldoctest
julia> A = [true false; true false]
2×2 Matrix{Bool}:
 1  0
 1  0

julia> all!([1; 1], A)
2-element Vector{Int64}:
 0
 0

julia> all!([1 1], A)
1×2 Matrix{Int64}:
 1  0
```
