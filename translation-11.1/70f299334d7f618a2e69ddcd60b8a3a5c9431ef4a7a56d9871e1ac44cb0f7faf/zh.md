```
Union{类型...}
```

`Union` 类型是一个抽象类型，它包含其任何参数类型的所有实例。这意味着 `T <: Union{T,S}` 和 `S <: Union{T,S}`。

与其他抽象类型一样，它不能被实例化，即使它的所有参数都是非抽象的。

# 示例

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 isa IntOrString # Int 的实例包含在联合中
true

julia> "Hello!" isa IntOrString # String 也包含在内
true

julia> 1.0 isa IntOrString # Float64 不包含，因为它既不是 Int 也不是 AbstractString
false
```

# 扩展帮助

与大多数其他参数化类型不同，联合在其参数中是协变的。例如，`Union{Real, String}` 是 `Union{Number, AbstractString}` 的子类型。

空联合 [`Union{}`](@ref) 是 Julia 的底层类型。
