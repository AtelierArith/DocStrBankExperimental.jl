```
BitArray(itr)
```

주어진 반복 가능한 객체로 생성된 [`BitArray`](@ref)를 구성합니다. 형태는 `itr` 객체에서 유추됩니다.

# 예제

```jldoctest
julia> BitArray([1 0; 0 1])
2×2 BitMatrix:
 1  0
 0  1

julia> BitArray(x+y == 3 for x = 1:2, y = 1:3)
2×3 BitMatrix:
 0  1  0
 1  0  0

julia> BitArray(x+y == 3 for x = 1:2 for y = 1:3)
6-element BitVector:
 0
 1
 0
 1
 0
 0
```
