```
foreach(f, c...) -> Nothing
```

Llama a la función `f` en cada elemento del iterable `c`. Para múltiples argumentos iterables, `f` se llama elemento por elemento, y la iteración se detiene cuando cualquier iterador ha terminado.

`foreach` debe usarse en lugar de [`map`](@ref) cuando no se necesitan los resultados de `f`, por ejemplo en `foreach(println, array)`.

# Ejemplos

```jldoctest
julia> tri = 1:3:7; res = Int[];

julia> foreach(x -> push!(res, x^2), tri)

julia> res
3-element Vector{Int64}:
  1
 16
 49

julia> foreach((x, y) -> println(x, " con ", y), tri, 'a':'z')
1 con a
4 con b
7 con c
```
