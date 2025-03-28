```
getindex(tipo[, elementos...])
```

Construye un arreglo unidimensional del tipo especificado. Esto se llama generalmente con la sintaxis `Tipo[]`. Los valores de los elementos se pueden especificar usando `Tipo[a,b,c,...]`.

# Ejemplos

```jldoctest
julia> Int8[1, 2, 3]
3-element Vector{Int8}:
 1
 2
 3

julia> getindex(Int8, 1, 2, 3)
3-element Vector{Int8}:
 1
 2
 3
```
