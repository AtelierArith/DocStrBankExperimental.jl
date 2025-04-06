```
invmod(n::Integer, T) where {T <: Base.BitInteger}
invmod(n::T) where {T <: Base.BitInteger}
```

`n`의 모듈러 역수를 정수 링의 타입 `T`에서 계산합니다. 즉, `2^N`로 모듈로 하며, 여기서 `N = 8*sizeof(T)`입니다 (예: `Int32`의 경우 `N = 32`). 다시 말해, 이러한 메서드는 다음과 같은 항등식을 만족합니다:

```
n * invmod(n) == 1
(n * invmod(n, T)) % T == 1
(n % T) * invmod(n, T) == 1
```

여기서 `*`는 정수 링 `T`에서의 모듈러 곱셈입니다.

정수 타입에 의해 암시된 모듈러스를 명시적인 값으로 지정하는 것은 종종 불편합니다. 왜냐하면 모듈러스는 정의상 타입으로 표현하기에는 너무 크기 때문입니다.

모듈러 역수는 https://arxiv.org/pdf/2204.04342.pdf에 설명된 알고리즘을 사용하여 일반적인 경우보다 훨씬 더 효율적으로 계산됩니다.

!!! compat "Julia 1.11"
    `invmod(n)` 및 `invmod(n, T)` 메서드는 Julia 1.11 이상이 필요합니다.

