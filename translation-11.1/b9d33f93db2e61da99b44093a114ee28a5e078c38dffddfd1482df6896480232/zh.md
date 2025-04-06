```
Unicode.isassigned(c) -> Bool
```

如果给定的字符或整数是已分配的 Unicode 代码点，则返回 `true`。

# 示例

```jldoctest
julia> Unicode.isassigned(101)
true

julia> Unicode.isassigned('\x01')
true
```
