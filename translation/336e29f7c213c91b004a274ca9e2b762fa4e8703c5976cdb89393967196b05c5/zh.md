```
sizeof(str::AbstractString)
```

字符串 `str` 的大小（以字节为单位）。等于 `str` 中代码单元的数量乘以 `str` 中一个代码单元的大小（以字节为单位）。

# 示例

```jldoctest
julia> sizeof("")
0

julia> sizeof("∀")
3
```
