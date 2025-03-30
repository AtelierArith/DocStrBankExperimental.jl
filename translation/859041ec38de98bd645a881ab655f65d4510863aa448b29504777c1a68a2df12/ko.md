```
DivideError()
```

정수 나눗셈이 0의 분모 값으로 시도되었습니다.

# 예제

```jldoctest
julia> 2/0
Inf

julia> div(2, 0)
ERROR: DivideError: integer division error
Stacktrace:
[...]
```
