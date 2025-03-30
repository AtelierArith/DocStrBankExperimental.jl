```
precision(num::AbstractFloat; base::Integer=2)
precision(T::Type; base::Integer=2)
```

부동 소수점 숫자의 정밀도를 가져옵니다. 이는 유효 숫자의 비트 수로 정의되며, 부동 소수점 타입 `T`의 정밀도(만약 `T`가 [`BigFloat`](@ref)와 같은 가변 정밀도 타입이라면 현재 기본값)입니다.

`base`가 지정되면 해당 진수에서 최대 해당하는 유효 숫자 자릿수를 반환합니다.

!!! compat "Julia 1.8"
    `base` 키워드는 최소한 Julia 1.8이 필요합니다.

