```
setindex!(collection, value, key...)
```

Almacena el valor dado en la clave o índice dado dentro de una colección. La sintaxis `a[i,j,...] = x` es convertida por el compilador a `(setindex!(a, x, i, j, ...); x)`.

# Ejemplos

```jldoctest
julia> a = Dict("a"=>1)
Dict{String, Int64} con 1 entrada:
  "a" => 1

julia> setindex!(a, 2, "b")
Dict{String, Int64} con 2 entradas:
  "b" => 2
  "a" => 1
```
