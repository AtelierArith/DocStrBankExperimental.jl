```
Core.Type{T}
```

`Core.Type` 是一个抽象类型，其所有类型对象都是它的实例。单例类型 `Core.Type{T}` 的唯一实例是对象 `T`。

# 示例

```jldoctest
julia> isa(Type{Float64}, Type)
true

julia> isa(Float64, Type)
true

julia> isa(Real, Type{Float64})
false

julia> isa(Real, Type{Real})
true
```
