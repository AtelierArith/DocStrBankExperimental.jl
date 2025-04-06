```
DivideError()
```

尝试进行整数除法，但分母值为 0。

# 示例

```jldoctest
julia> 2/0
Inf

julia> div(2, 0)
ERROR: DivideError: integer division error
Stacktrace:
[...]
```
