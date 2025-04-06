```
digits!(array, n::Integer; base::Integer = 10)
```

Llena un arreglo con los dígitos de `n` en la base dada. Los dígitos más significativos están en índices más altos. Si la longitud del arreglo es insuficiente, se llenan los dígitos menos significativos hasta la longitud del arreglo. Si la longitud del arreglo es excesiva, la porción excedente se llena con ceros.

# Ejemplos

```jldoctest
julia> digits!([2, 2, 2, 2], 10, base = 2)
4-element Vector{Int64}:
 0
 1
 0
 1

julia> digits!([2, 2, 2, 2, 2, 2], 10, base = 2)
6-element Vector{Int64}:
 0
 1
 0
 1
 0
 0
```
