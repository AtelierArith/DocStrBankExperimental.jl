```
DomainError(val)
DomainError(val, msg)
```

参数 `val` 对于一个函数或构造函数来说超出了有效域。

# 示例

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt 被调用时使用了一个负的实数参数，但只有在使用复数参数时才会返回复数结果。尝试使用 sqrt(Complex(x))。
Stacktrace:
[...]
```
