```
parent(A)
```

뷰의 기본 부모 객체를 반환합니다. `SubArray`, `SubString`, `ReshapedArray` 또는 `LinearAlgebra.Transpose` 유형의 객체의 부모는 객체 생성 시 `view`, `reshape`, `transpose` 등에 인수로 전달된 것입니다. 입력이 래핑된 객체가 아닌 경우 입력 자체를 반환합니다. 입력이 여러 번 래핑된 경우 가장 바깥쪽 래퍼만 제거됩니다.

# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> V = view(A, 1:2, :)
2×2 view(::Matrix{Int64}, 1:2, :) with eltype Int64:
 1  2
 3  4

julia> parent(V)
2×2 Matrix{Int64}:
 1  2
 3  4
```
