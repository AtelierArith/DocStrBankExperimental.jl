```
reduce(f, A::AbstractArray; dims=:, [init])
```

Reduce la función de 2 argumentos `f` a lo largo de las dimensiones de `A`. `dims` es un vector que especifica las dimensiones a reducir, y el argumento de palabra clave `init` es el valor inicial a utilizar en las reducciones. Para `+`, `*`, `max` y `min`, el argumento `init` es opcional.

La asociatividad de la reducción depende de la implementación; si necesitas una asociatividad particular, por ejemplo, de izquierda a derecha, deberías escribir tu propio bucle o considerar usar [`foldl`](@ref) o [`foldr`](@ref). Consulta la documentación para [`reduce`](@ref).

# Ejemplos

```jldoctest
julia> a = reshape(Vector(1:16), (4,4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> reduce(max, a, dims=2)
4×1 Matrix{Int64}:
 13
 14
 15
 16

julia> reduce(max, a, dims=1)
1×4 Matrix{Int64}:
 4  8  12  16
```
