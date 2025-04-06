```
IdSet{T}([itr])
IdSet()
```

IdSet{T}() construye un conjunto (ver [`Set`](@ref)) utilizando `===` como igualdad con valores del tipo `T`.

En el ejemplo a continuación, los valores son todos `isequal` por lo que se sobrescriben en el `Set` ordinario. El `IdSet` compara por `===` y por lo tanto preserva los 3 valores diferentes.

# Ejemplos

```jldoctest; filter = r"\n\s*(1|1\.0|true)"
julia> Set(Any[true, 1, 1.0])
Set{Any} con 1 elemento:
  1.0

julia> IdSet{Any}(Any[true, 1, 1.0])
IdSet{Any} con 3 elementos:
  1.0
  1
  true
```
