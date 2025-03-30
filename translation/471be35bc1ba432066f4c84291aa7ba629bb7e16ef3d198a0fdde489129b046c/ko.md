```
InexactError(name::Symbol, T, val)
```

`val`을(type `T`로) 정확하게 변환할 수 없습니다. 함수 `name`의 메서드에서 발생했습니다.

# 예제

```jldoctest
julia> convert(Float64, 1+2im)
ERROR: InexactError: Float64(1 + 2im)
Stacktrace:
[...]
```
