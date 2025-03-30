```
promote(xs...)
```

将所有参数转换为一个共同类型，并将它们全部返回（作为一个元组）。如果没有参数可以转换，则会引发错误。

另请参见: [`promote_type`](@ref), [`promote_rule`](@ref).

# 示例

```jldoctest
julia> promote(Int8(1), Float16(4.5), Float32(4.1))
(1.0f0, 4.5f0, 4.1f0)

julia> promote_type(Int8, Float16, Float32)
Float32

julia> reduce(Base.promote_typejoin, (Int8, Float16, Float32))
Real

julia> promote(1, "x")
ERROR: promotion of types Int64 and String failed to change any arguments
[...]

julia> promote_type(Int, String)
Any
```
