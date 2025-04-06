```
real(T::Type)
```

返回表示类型 `T` 的值的实部的类型。例如：对于 `T == Complex{R}`，返回 `R`。等价于 `typeof(real(zero(T)))`。

# 示例

```jldoctest
julia> real(Complex{Int})
Int64

julia> real(Float64)
Float64
```
