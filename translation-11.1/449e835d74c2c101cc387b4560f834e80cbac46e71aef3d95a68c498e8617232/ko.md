```
nextind(A, i)
```

`A`에서 `i` 다음의 인덱스를 반환합니다. 반환된 인덱스는 종종 정수 `i`에 대해 `i + 1`과 동일합니다. 이 함수는 일반적인 코드에 유용할 수 있습니다.

!!! 경고     반환된 인덱스가 범위를 벗어날 수 있습니다. [`checkbounds`](@ref) 사용을 고려하세요.

또한: [`prevind`](@ref).

# 예제

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nextind(x, 1) # 유효한 결과
2

julia> nextind(x, 4) # 유효하지 않은 결과
5

julia> nextind(x, CartesianIndex(1, 1)) # 유효한 결과
CartesianIndex(2, 1)

julia> nextind(x, CartesianIndex(2, 2)) # 유효하지 않은 결과
CartesianIndex(1, 3)
```
