```
maxintfloat(T=Float64)
```

주어진 부동 소수점 유형 `T`(기본값은 `Float64`)에서 정확하게 표현되는 가장 큰 연속 정수 값의 부동 소수점 숫자입니다.

즉, `maxintfloat`는 `n+1`이 유형 `T`에서 *정확하게* 표현되지 않는 가장 작은 양의 정수 값의 부동 소수점 숫자 `n`을 반환합니다.

`Integer` 유형의 값이 필요할 경우, `Integer(maxintfloat(T))`를 사용하십시오.
