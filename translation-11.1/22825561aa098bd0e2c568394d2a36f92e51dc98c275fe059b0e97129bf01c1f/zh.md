```
x | y
```

按位或。实现了[三值逻辑](https://en.wikipedia.org/wiki/Three-valued_logic)，如果一个操作数是`missing`而另一个是`false`，则返回[`missing`](@ref)。

另请参见：[`&`](@ref)，[`xor`](@ref)，[`||`](@ref)。

# 示例

```jldoctest
julia> 4 | 10
14

julia> 4 | 1
5

julia> true | missing
true

julia> false | missing
missing
```
