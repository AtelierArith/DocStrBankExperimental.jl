```
>>(B::BitVector, n) -> BitVector
```

오른쪽 비트 시프트 연산자, `B >> n`. `n >= 0`인 경우, 결과는 `B`의 요소가 `n` 위치만큼 앞으로 이동하며, `false` 값으로 채워집니다. `n < 0`인 경우, 요소가 뒤로 이동합니다. `B << -n`과 동일합니다.

# 예제

```jldoctest
julia> B = BitVector([true, false, true, false, false])
5-element BitVector:
 1
 0
 1
 0
 0

julia> B >> 1
5-element BitVector:
 0
 1
 0
 1
 0

julia> B >> -1
5-element BitVector:
 0
 1
 0
 0
 0
```
