```
floatmin(T = Float64)
```

返回浮点类型 `T` 可表示的最小正正规数。

# 示例

```jldoctest
julia> floatmin(Float16)
Float16(6.104e-5)

julia> floatmin(Float32)
1.1754944f-38

julia> floatmin()
2.2250738585072014e-308
```
