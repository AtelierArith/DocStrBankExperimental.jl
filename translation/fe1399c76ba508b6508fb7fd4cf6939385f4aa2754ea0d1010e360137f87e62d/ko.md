```
DomainError(val)
DomainError(val, msg)
```

함수나 생성자에 대한 인수 `val`이 유효한 범위를 벗어났습니다.

# 예제

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt는 음의 실수 인수로 호출되었지만 복소수 인수로 호출될 때만 복소수 결과를 반환합니다. sqrt(Complex(x))를 시도해 보세요.
Stacktrace:
[...]
```
