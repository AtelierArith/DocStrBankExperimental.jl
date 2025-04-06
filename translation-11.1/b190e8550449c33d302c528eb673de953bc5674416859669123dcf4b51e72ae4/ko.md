```
RoundFromZero
```

제로에서 멀리 반올림합니다.

!!! compat "Julia 1.9"
    `RoundFromZero`는 최소한 Julia 1.9가 필요합니다. 이전 버전은 `BigFloat`에 대해서만 `RoundFromZero`를 지원합니다.


# 예제

```jldoctest
julia> BigFloat("1.0000000000000001", 5, RoundFromZero)
1.06
```
