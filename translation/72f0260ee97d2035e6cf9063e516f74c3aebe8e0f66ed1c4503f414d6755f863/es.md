```
vcat(A...)
```

Concatena arreglos o números verticalmente. Equivalente a [`cat`](@ref)`(A...; dims=1)`, y a la sintaxis `[a; b; c]`.

Para concatenar un gran vector de arreglos, `reduce(vcat, A)` llama a un método eficiente cuando `A isa AbstractVector{<:AbstractVecOrMat}`, en lugar de trabajar de manera par.

Véase también [`hcat`](@ref), [`Iterators.flatten`](@ref), [`stack`](@ref).

# Ejemplos

```jldoctest
julia> v = vcat([1,2], [3,4])
4-element Vector{Int64}:
 1
 2
 3
 4

julia> v == vcat(1, 2, [3,4])  # acepta números
true

julia> v == [1; 2; [3,4]]  # sintaxis para la misma operación
true

julia> summary(ComplexF64[1; 2; [3,4]])  # sintaxis para suministrar el tipo de elemento
"4-element Vector{ComplexF64}"

julia> vcat(range(1, 2, length=3))  # recoge rangos perezosos
3-element Vector{Float64}:
 1.0
 1.5
 2.0

julia> two = ([10, 20, 30]', Float64[4 5 6; 7 8 9])  # vector fila y una matriz
([10 20 30], [4.0 5.0 6.0; 7.0 8.0 9.0])

julia> vcat(two...)
3×3 Matrix{Float64}:
 10.0  20.0  30.0
  4.0   5.0   6.0
  7.0   8.0   9.0

julia> vs = [[1, 2], [3, 4], [5, 6]];

julia> reduce(vcat, vs)  # más eficiente que vcat(vs...)
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6

julia> ans == collect(Iterators.flatten(vs))
true
```
