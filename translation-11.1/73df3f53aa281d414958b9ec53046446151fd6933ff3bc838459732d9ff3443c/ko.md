```
ismutabletype(T) -> Bool
```

타입 `T`가 가변 타입으로 선언되었는지 여부를 결정합니다(즉, `mutable struct` 키워드를 사용하여). 만약 `T`가 타입이 아니라면 `false`를 반환합니다.

!!! compat "Julia 1.7"
    이 함수는 최소한 Julia 1.7이 필요합니다.

