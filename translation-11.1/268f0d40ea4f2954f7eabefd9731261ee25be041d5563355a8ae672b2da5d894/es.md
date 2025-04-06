```
Transponer
```

Tipo de envoltura perezosa para una vista transpuesta del objeto de álgebra lineal subyacente, generalmente un `AbstractVector`/`AbstractMatrix`. Por lo general, el constructor `Transpose` no debe ser llamado directamente, usa [`transpose`](@ref) en su lugar. Para materializar la vista, usa [`copy`](@ref).

Este tipo está destinado para uso en álgebra lineal; para manipulación de datos general, consulta [`permutedims`](@ref Base.permutedims).

# Ejemplos

```jldoctest
julia> A = [2 3; 0 0]
2×2 Matrix{Int64}:
 2  3
 0  0

julia> Transpose(A)
2×2 transpose(::Matrix{Int64}) with eltype Int64:
 2  0
 3  0
```
