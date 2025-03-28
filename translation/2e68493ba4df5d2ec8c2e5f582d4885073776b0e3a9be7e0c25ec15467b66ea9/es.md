```
getindex(collection, key...)
```

Recupera el(los) valor(es) almacenado(s) en la clave o índice dado dentro de una colección. La sintaxis `a[i,j,...]` es convertida por el compilador a `getindex(a, i, j, ...)`.

Véase también [`get`](@ref), [`keys`](@ref), [`eachindex`](@ref).

# Ejemplos

```jldoctest
julia> A = Dict("a" => 1, "b" => 2)
Dict{String, Int64} con 2 entradas:
  "b" => 2
  "a" => 1

julia> getindex(A, "a")
1
```
