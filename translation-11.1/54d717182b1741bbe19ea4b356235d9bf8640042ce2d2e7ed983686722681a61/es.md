```
hcat(A...)
```

Concatena arreglos o números horizontalmente. Equivalente a [`cat`](@ref)`(A...; dims=2)`, y a la sintaxis `[a b c]` o `[a;; b;; c]`.

Para un vector grande de arreglos, `reduce(hcat, A)` llama a un método eficiente cuando `A isa AbstractVector{<:AbstractVecOrMat}`. Para un vector de vectores, esto también se puede escribir como [`stack`](@ref)`(A)`.

Véase también [`vcat`](@ref), [`hvcat`](@ref).

# Ejemplos

```jldoctest
julia> hcat([1,2], [3,4], [5,6])
2×3 Matrix{Int64}:
 1  3  5
 2  4  6

julia> hcat(1, 2, [30 40], [5, 6, 7]')  # acepta números
1×7 Matrix{Int64}:
 1  2  30  40  5  6  7

julia> ans == [1 2 [30 40] [5, 6, 7]']  # sintaxis para la misma operación
true

julia> Float32[1 2 [30 40] [5, 6, 7]']  # sintaxis para suministrar el eltype
1×7 Matrix{Float32}:
 1.0  2.0  30.0  40.0  5.0  6.0  7.0

julia> ms = [zeros(2,2), [1 2; 3 4], [50 60; 70 80]];

julia> reduce(hcat, ms)  # más eficiente que hcat(ms...)
2×6 Matrix{Float64}:
 0.0  0.0  1.0  2.0  50.0  60.0
 0.0  0.0  3.0  4.0  70.0  80.0

julia> stack(ms) |> summary  # no concuerda en un vector de matrices
"2×2×3 Array{Float64, 3}"

julia> hcat(Int[], Int[], Int[])  # vectores vacíos, cada uno de tamaño (0,)
0×3 Matrix{Int64}

julia> hcat([1.1, 9.9], Matrix(undef, 2, 0))  # hcat con matriz 2×0 vacía
2×1 Matrix{Any}:
 1.1
 9.9
```
