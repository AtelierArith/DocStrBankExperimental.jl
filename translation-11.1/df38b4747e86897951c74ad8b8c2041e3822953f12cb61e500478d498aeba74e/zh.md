```
x & y
```

按位与。实现了[三值逻辑](https://en.wikipedia.org/wiki/Three-valued_logic)，如果一个操作数是`missing`而另一个是`true`，则返回[`missing`](@ref)。为函数应用形式添加括号：`(&)(x, y)`。

另请参见：[`|`](@ref)，[`xor`](@ref)，[`&&`](@ref)。

# 示例

```jldoctest
julia> 4 & 10
0

julia> 4 & 12
4

julia> true & missing
missing

julia> false & missing
false
```
