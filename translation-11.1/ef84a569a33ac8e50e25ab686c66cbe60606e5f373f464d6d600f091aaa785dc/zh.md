```
nameof(m::Module) -> Symbol
```

获取 `Module` 的名称作为一个 [`Symbol`](@ref)。

# 示例

```jldoctest
julia> nameof(Base.Broadcast)
:Broadcast
```
