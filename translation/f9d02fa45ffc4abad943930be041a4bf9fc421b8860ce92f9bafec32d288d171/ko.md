```
bitrand([rng=default_rng()], [dims...])
```

무작위 부울 값의 `BitArray`를 생성합니다.

# 예제

```jldoctest
julia> bitrand(Xoshiro(123), 10)
10-element BitVector:
 0
 1
 0
 1
 0
 1
 0
 0
 1
 1
```
