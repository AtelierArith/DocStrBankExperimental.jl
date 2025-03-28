```
stack(iter; [dims])
```

Combina una colección de arreglos (u otros objetos iterables) de igual tamaño en un solo arreglo más grande, organizándolos a lo largo de una o más nuevas dimensiones.

Por defecto, los ejes de los elementos se colocan primero, dando `size(result) = (size(first(iter))..., size(iter)...)`. Esto tiene el mismo orden de elementos que [`Iterators.flatten`](@ref)`(iter)`.

Con la palabra clave `dims::Integer`, en su lugar, el elemento `i` de `iter` se convierte en el corte [`selectdim`](@ref)`(result, dims, i)`, de modo que `size(result, dims) == length(iter)`. En este caso, `stack` revierte la acción de [`eachslice`](@ref) con los mismos `dims`.

Las diversas funciones [`cat`](@ref) también combinan arreglos. Sin embargo, todas estas extienden las dimensiones existentes (posiblemente triviales) de los arreglos, en lugar de colocar los arreglos a lo largo de nuevas dimensiones. También aceptan arreglos como argumentos separados, en lugar de una sola colección.

!!! compat "Julia 1.9"
    Esta función requiere al menos Julia 1.9.


# Ejemplos

```jldoctest
julia> vecs = (1:2, [30, 40], Float32[500, 600]);

julia> mat = stack(vecs)
2×3 Matrix{Float32}:
 1.0  30.0  500.0
 2.0  40.0  600.0

julia> mat == hcat(vecs...) == reduce(hcat, collect(vecs))
true

julia> vec(mat) == vcat(vecs...) == reduce(vcat, collect(vecs))
true

julia> stack(zip(1:4, 10:99))  # acepta cualquier iterador de iteradores
2×4 Matrix{Int64}:
  1   2   3   4
 10  11  12  13

julia> vec(ans) == collect(Iterators.flatten(zip(1:4, 10:99)))
true

julia> stack(vecs; dims=1)  # a diferencia de cualquier función cat, el 1er eje de vecs[1] es el 2do eje del resultado
3×2 Matrix{Float32}:
   1.0    2.0
  30.0   40.0
 500.0  600.0

julia> x = rand(3,4);

julia> x == stack(eachcol(x)) == stack(eachrow(x), dims=1)  # inverso de eachslice
true
```

Ejemplos de dimensiones superiores:

```jldoctest
julia> A = rand(5, 7, 11);

julia> E = eachslice(A, dims=2);  # un vector de matrices

julia> (element = size(first(E)), container = size(E))
(element = (5, 11), container = (7,))

julia> stack(E) |> size
(5, 11, 7)

julia> stack(E) == stack(E; dims=3) == cat(E...; dims=3)
true

julia> A == stack(E; dims=2)
true

julia> M = (fill(10i+j, 2, 3) for i in 1:5, j in 1:7);

julia> (element = size(first(M)), container = size(M))
(element = (2, 3), container = (5, 7))

julia> stack(M) |> size  # mantiene todas las dimensiones
(2, 3, 5, 7)

julia> stack(M; dims=1) |> size  # vec(container) a lo largo de dims=1
(35, 2, 3)

julia> hvcat(5, M...) |> size  # hvcat coloca matrices una al lado de la otra
(14, 15)
```
