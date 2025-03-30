```
isa(x, type) -> Bool
```

确定 `x` 是否为给定的 `type`。也可以用作中缀运算符，例如 `x isa type`。

# 示例

```jldoctest
julia> isa(1, Int)
true

julia> isa(1, Matrix)
false

julia> isa(1, Char)
false

julia> isa(1, Number)
true

julia> 1 isa Number
true
```
