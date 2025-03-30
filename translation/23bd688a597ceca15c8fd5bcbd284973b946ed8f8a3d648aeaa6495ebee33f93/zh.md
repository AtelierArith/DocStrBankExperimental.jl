```
isconcretetype(T)
```

确定类型 `T` 是否为具体类型，这意味着它可以有直接实例（值 `x` 使得 `typeof(x) === T`）。请注意，这并不是 `isabstracttype(T)` 的否定。如果 `T` 不是一个类型，则返回 `false`。

另请参见：[`isbits`](@ref), [`isabstracttype`](@ref), [`issingletontype`](@ref)。

# 示例

```jldoctest
julia> isconcretetype(Complex)
false

julia> isconcretetype(Complex{Float32})
true

julia> isconcretetype(Vector{Complex})
true

julia> isconcretetype(Vector{Complex{Float32}})
true

julia> isconcretetype(Union{})
false

julia> isconcretetype(Union{Int,String})
false
```
