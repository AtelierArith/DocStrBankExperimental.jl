```
Integer <: Real
```

所有整数的抽象超类型（例如 [`Signed`](@ref)、[`Unsigned`](@ref) 和 [`Bool`](@ref)）。

另请参见 [`isinteger`](@ref)、[`trunc`](@ref)、[`div`](@ref)。

# 示例

```
julia> 42 isa Integer
true

julia> 1.0 isa Integer
false

julia> isinteger(1.0)
true
```
