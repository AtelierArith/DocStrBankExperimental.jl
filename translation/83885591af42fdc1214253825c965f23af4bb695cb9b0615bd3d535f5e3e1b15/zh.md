```
issubnormal(f) -> Bool
```

测试一个浮点数是否是次正规数。

当一个IEEE浮点数的指数位为零且其有效数字不为零时，它是[次正规](https://en.wikipedia.org/wiki/Subnormal_number)的。

# 示例

```jldoctest
julia> floatmin(Float32)
1.1754944f-38

julia> issubnormal(1.0f-37)
false

julia> issubnormal(1.0f-38)
true
```
