```
typeassert(x, type)
```

`x isa type`가 아닐 경우 [`TypeError`](@ref)를 발생시킵니다. 구문 `x::type`은 이 함수를 호출합니다.

# 예제

```jldoctest
julia> typeassert(2.5, Int)
ERROR: TypeError: in typeassert, expected Int64, got a value of type Float64
Stacktrace:
[...]
```
