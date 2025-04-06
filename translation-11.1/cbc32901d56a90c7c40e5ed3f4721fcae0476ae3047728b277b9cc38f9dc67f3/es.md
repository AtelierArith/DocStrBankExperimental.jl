```
IdDict([itr])
```

`IdDict{K,V}()` construye una tabla hash utilizando [`objectid`](@ref) como hash y `===` como igualdad con claves del tipo `K` y valores del tipo `V`. Consulta [`Dict`](@ref) para más ayuda y [`IdSet`](@ref) para la versión de conjunto de esto.

En el ejemplo a continuación, las claves de `Dict` son todas `isequal` y, por lo tanto, se hashan de la misma manera, así que se sobrescriben. El `IdDict` hash por id de objeto, y por lo tanto preserva las 3 claves diferentes.

# Ejemplos

```julia-repl
julia> Dict(true => "yes", 1 => "no", 1.0 => "maybe")
Dict{Real, String} con 1 entrada:
  1.0 => "maybe"

julia> IdDict(true => "yes", 1 => "no", 1.0 => "maybe")
IdDict{Any, String} con 3 entradas:
  true => "yes"
  1.0  => "maybe"
  1    => "no"
```
