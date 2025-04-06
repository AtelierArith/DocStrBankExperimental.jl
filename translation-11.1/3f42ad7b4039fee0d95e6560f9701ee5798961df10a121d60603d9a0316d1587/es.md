```
Array{T}(undef, dims)
Array{T,N}(undef, dims)
```

Construye un [`Array`](@ref) no inicializado de `N` dimensiones que contiene elementos del tipo `T`. `N` puede ser proporcionado explícitamente, como en `Array{T,N}(undef, dims)`, o ser determinado por la longitud o el número de `dims`. `dims` puede ser una tupla o una serie de argumentos enteros que corresponden a las longitudes en cada dimensión. Si el rango `N` se proporciona explícitamente, entonces debe coincidir con la longitud o el número de `dims`. Aquí [`undef`](@ref) es el [`UndefInitializer`](@ref).

# Ejemplos

```julia-repl
julia> A = Array{Float64, 2}(undef, 2, 3) # N dado explícitamente
2×3 Matrix{Float64}:
 6.90198e-310  6.90198e-310  6.90198e-310
 6.90198e-310  6.90198e-310  0.0

julia> B = Array{Float64}(undef, 4) # N determinado por la entrada
4-element Vector{Float64}:
   2.360075077e-314
 NaN
   2.2671131793e-314
   2.299821756e-314

julia> similar(B, 2, 4, 1) # usa typeof(B), y el tamaño dado
2×4×1 Array{Float64, 3}:
[:, :, 1] =
 2.26703e-314  2.26708e-314  0.0           2.80997e-314
 0.0           2.26703e-314  2.26708e-314  0.0
```
