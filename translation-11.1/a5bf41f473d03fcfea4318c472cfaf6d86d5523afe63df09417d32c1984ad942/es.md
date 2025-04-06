```
partialsort!(v, k; by=identity, lt=isless, rev=false)
```

Ordena parcialmente el vector `v` en su lugar de modo que el valor en el índice `k` (o rango de valores adyacentes si `k` es un rango) ocurra en la posición donde aparecería si el arreglo estuviera completamente ordenado. Si `k` es un índice único, ese valor se devuelve; si `k` es un rango, se devuelve un arreglo de valores en esos índices. Ten en cuenta que `partialsort!` puede no ordenar completamente el arreglo de entrada.

Para los argumentos de palabra clave, consulta la documentación de [`sort!`](@ref).

# Ejemplos

```jldoctest
julia> a = [1, 2, 4, 3, 4]
5-element Vector{Int64}:
 1
 2
 4
 3
 4

julia> partialsort!(a, 4)
4

julia> a
5-element Vector{Int64}:
 1
 2
 3
 4
 4

julia> a = [1, 2, 4, 3, 4]
5-element Vector{Int64}:
 1
 2
 4
 3
 4

julia> partialsort!(a, 4, rev=true)
2

julia> a
5-element Vector{Int64}:
 4
 4
 3
 2
 1
```
