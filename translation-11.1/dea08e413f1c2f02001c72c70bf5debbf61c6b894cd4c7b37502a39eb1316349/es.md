```
Adjunto
```

Tipo de envoltura perezosa para una vista adjunta del objeto de álgebra lineal subyacente, generalmente un `AbstractVector`/`AbstractMatrix`. Por lo general, el constructor `Adjoint` no debe ser llamado directamente, usa [`adjoint`](@ref) en su lugar. Para materializar la vista, usa [`copy`](@ref).

Este tipo está destinado para uso en álgebra lineal; para manipulación de datos general, consulta [`permutedims`](@ref Base.permutedims).

# Ejemplos

```jldoctest
julia> A = [3+2im 9+2im; 0 0]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 0+0im  0+0im

julia> Adjoint(A)
2×2 adjoint(::Matrix{Complex{Int64}}) con el tipo eltype Complex{Int64}:
 3-2im  0+0im
 9-2im  0+0im
```
