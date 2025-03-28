```
Dict([itr])
```

`Dict{K,V}()` construye una tabla hash con claves del tipo `K` y valores del tipo `V`. Las claves se comparan con [`isequal`](@ref) y se hash con [`hash`](@ref).

Dado un único argumento iterable, construye un [`Dict`](@ref) cuyas parejas clave-valor se toman de tuplas de 2 elementos `(clave, valor)` generadas por el argumento.

# Ejemplos

```jldoctest
julia> Dict([("A", 1), ("B", 2)])
Dict{String, Int64} con 2 entradas:
  "B" => 2
  "A" => 1
```

Alternativamente, se puede pasar una secuencia de argumentos en pareja.

```jldoctest
julia> Dict("A"=>1, "B"=>2)
Dict{String, Int64} con 2 entradas:
  "B" => 2
  "A" => 1
```

!!! advertencia
    Se permite que las claves sean mutables, pero si mutas las claves almacenadas, la tabla hash puede volverse internamente inconsistente, en cuyo caso el `Dict` no funcionará correctamente. [`IdDict`](@ref) puede ser una alternativa si necesitas mutar claves.

