```
isabstracttype(T)
```

确定类型 `T` 是否被声明为抽象类型（即使用 `abstract type` 语法）。请注意，这并不是 `isconcretetype(T)` 的否定。如果 `T` 不是一个类型，则返回 `false`。

# 示例

```jldoctest
julia> isabstracttype(AbstractArray)
true

julia> isabstracttype(Vector)
false
```
