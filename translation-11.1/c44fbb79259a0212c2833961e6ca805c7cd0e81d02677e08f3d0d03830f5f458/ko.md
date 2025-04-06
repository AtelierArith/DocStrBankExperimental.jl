```
circshift(A, shifts)
```

배열의 데이터를 순환적으로 이동, 즉 회전합니다. 두 번째 인자는 각 차원에서 이동할 양을 제공하는 튜플 또는 벡터이거나, 첫 번째 차원에서만 이동할 정수입니다.

또한 참조: [`circshift!`](@ref), [`circcopy!`](@ref), [`bitrotate`](@ref), [`<<`](@ref).

# 예제

```jldoctest
julia> b = reshape(Vector(1:16), (4,4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> circshift(b, (0,2))
4×4 Matrix{Int64}:
  9  13  1  5
 10  14  2  6
 11  15  3  7
 12  16  4  8

julia> circshift(b, (-1,0))
4×4 Matrix{Int64}:
 2  6  10  14
 3  7  11  15
 4  8  12  16
 1  5   9  13

julia> a = BitArray([true, true, false, false, true])
5-element BitVector:
 1
 1
 0
 0
 1

julia> circshift(a, 1)
5-element BitVector:
 1
 1
 1
 0
 0

julia> circshift(a, -1)
5-element BitVector:
 1
 0
 0
 1
 1
```
