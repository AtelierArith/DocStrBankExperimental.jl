```
copy(A::Transpose)
copy(A::Adjoint)
```

Evalúa de manera ansiosa la transposición/adjunto de matriz perezosa. Ten en cuenta que la transposición se aplica recursivamente a los elementos.

Esta operación está destinada para el uso en álgebra lineal; para la manipulación de datos general, consulta [`permutedims`](@ref Base.permutedims), que no es recursiva.

# Ejemplos

```jldoctest
julia> A = [1 2im; -3im 4]
2×2 Matrix{Complex{Int64}}:
 1+0im  0+2im
 0-3im  4+0im

julia> T = transpose(A)
2×2 transpose(::Matrix{Complex{Int64}}) with eltype Complex{Int64}:
 1+0im  0-3im
 0+2im  4+0im

julia> copy(T)
2×2 Matrix{Complex{Int64}}:
 1+0im  0-3im
 0+2im  4+0im
```
