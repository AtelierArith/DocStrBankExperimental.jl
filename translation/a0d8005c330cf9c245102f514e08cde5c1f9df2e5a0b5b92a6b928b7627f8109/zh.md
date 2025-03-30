```
<:(T1, T2)
```

子类型运算符：仅当类型 `T1` 的所有值也属于类型 `T2` 时返回 `true`。

# 示例

```jldoctest
julia> Float64 <: AbstractFloat
true

julia> Vector{Int} <: AbstractArray
true

julia> Matrix{Float64} <: Matrix{AbstractFloat}
false
```
