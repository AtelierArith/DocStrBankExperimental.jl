```
parentmodule(m::Module) -> Module
```

获取模块的封闭 `Module`。`Main` 是它自己的父模块。

另请参见：[`names`](@ref), [`nameof`](@ref), [`fullname`](@ref), [`@__MODULE__`](@ref)。

# 示例

```jldoctest
julia> parentmodule(Main)
Main

julia> parentmodule(Base.Broadcast)
Base
```
