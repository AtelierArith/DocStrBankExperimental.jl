```
cat(A...; dims)
```

Concatena los arreglos de entrada a lo largo de las dimensiones especificadas en `dims`.

A lo largo de una dimensión `d in dims`, el tamaño del arreglo de salida es `sum(size(a,d) for a in A)`. A lo largo de otras dimensiones, todos los arreglos de entrada deben tener el mismo tamaño, que también será el tamaño del arreglo de salida a lo largo de esas dimensiones.

Si `dims` es un solo número, los diferentes arreglos están empaquetados de manera compacta a lo largo de esa dimensión. Si `dims` es un iterable que contiene varias dimensiones, las posiciones a lo largo de estas dimensiones se incrementan simultáneamente para cada arreglo de entrada, llenando con ceros en otros lugares. Esto permite construir matrices diagonales por bloques como `cat(matrices...; dims=(1,2))`, y sus análogos de mayor dimensión.

El caso especial `dims=1` es [`vcat`](@ref), y `dims=2` es [`hcat`](@ref). Ver también [`hvcat`](@ref), [`hvncat`](@ref), [`stack`](@ref), [`repeat`](@ref).

La palabra clave también acepta `Val(dims)`.

!!! compat "Julia 1.8"
    Para múltiples dimensiones `dims = Val(::Tuple)` se agregó en Julia 1.8.


# Ejemplos

Concatena dos arreglos en diferentes dimensiones:

```jldoctest
julia> a = [1 2 3]
1×3 Matrix{Int64}:
 1  2  3

julia> b = [4 5 6]
1×3 Matrix{Int64}:
 4  5  6

julia> cat(a, b; dims=1)
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> cat(a, b; dims=2)
1×6 Matrix{Int64}:
 1  2  3  4  5  6

julia> cat(a, b; dims=(1, 2))
2×6 Matrix{Int64}:
 1  2  3  0  0  0
 0  0  0  4  5  6
```

# Ayuda Extendida

Concatena arreglos 3D:

```jldoctest
julia> a = ones(2, 2, 3);

julia> b = ones(2, 2, 4);

julia> c = cat(a, b; dims=3);

julia> size(c) == (2, 2, 7)
true
```

Concatena arreglos de diferentes tamaños:

```jldoctest
julia> cat([1 2; 3 4], [pi, pi], fill(10, 2,3,1); dims=2)  # igual que hcat
2×6×1 Array{Float64, 3}:
[:, :, 1] =
 1.0  2.0  3.14159  10.0  10.0  10.0
 3.0  4.0  3.14159  10.0  10.0  10.0
```

Construye una matriz diagonal por bloques:

```
julia> cat(true, trues(2,2), trues(4)', dims=(1,2))  # diagonal por bloques
4×7 Matrix{Bool}:
 1  0  0  0  0  0  0
 0  1  1  0  0  0  0
 0  1  1  0  0  0  0
 0  0  0  1  1  1  1
```

```
julia> cat(1, [2], [3;;]; dims=Val(2))
1×3 Matrix{Int64}:
 1  2  3
```

!!! note
    `cat` no une dos cadenas, es posible que desees usar `*`.


```jldoctest
julia> a = "aaa";

julia> b = "bbb";

julia> cat(a, b; dims=1)
2-element Vector{String}:
 "aaa"
 "bbb"

julia> cat(a, b; dims=2)
1×2 Matrix{String}:
 "aaa"  "bbb"

julia> a * b
"aaabbb"
```
