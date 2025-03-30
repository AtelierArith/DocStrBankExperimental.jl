```
!(x)
```

布尔非。实现了[三值逻辑](https://en.wikipedia.org/wiki/Three-valued_logic)，如果 `x` 是 `missing`，则返回 [`missing`](@ref)。

另见 [`~`](@ref) 进行按位非。

# 示例

```jldoctest
julia> !true
false

julia> !false
true

julia> !missing
missing

julia> .![true false true]
1×3 BitMatrix:
 0  1  0
```
