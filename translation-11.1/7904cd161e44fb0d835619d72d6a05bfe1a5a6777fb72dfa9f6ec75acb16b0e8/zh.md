```
isassigned(array, i) -> Bool
```

测试给定数组是否有与索引 `i` 关联的值。如果索引超出范围或具有未定义的引用，则返回 `false`。

# 示例

```jldoctest
julia> isassigned(rand(3, 3), 5)
true

julia> isassigned(rand(3, 3), 3 * 3 + 1)
false

julia> mutable struct Foo end

julia> v = similar(rand(3), Foo)
3-element Vector{Foo}:
 #undef
 #undef
 #undef

julia> isassigned(v, 1)
false
```
