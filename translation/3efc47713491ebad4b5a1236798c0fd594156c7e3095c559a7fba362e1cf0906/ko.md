```
setprecision(f::Function, [T=BigFloat,] precision::Integer; base=2)
```

주어진 `f`의 기간 동안 `T` 산술 정밀도(주어진 `base`)를 변경합니다. 이는 논리적으로 다음과 같습니다:

```
old = precision(BigFloat)
setprecision(BigFloat, precision)
f()
setprecision(BigFloat, old)
```

종종 `setprecision(T, precision) do ... end`와 같이 사용됩니다.

참고: `nextfloat()`, `prevfloat()`는 `setprecision`에서 언급한 정밀도를 사용하지 않습니다.

!!! compat "Julia 1.8"
    `base` 키워드는 최소한 Julia 1.8이 필요합니다.

