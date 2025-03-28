```
filter(f, d::AbstractDict)
```

Devuelve una copia de `d`, eliminando elementos para los cuales `f` es `false`. La función `f` recibe pares `key=>value`.

# Ejemplos

```jldoctest
julia> d = Dict(1=>"a", 2=>"b")
Dict{Int64, String} con 2 entradas:
  2 => "b"
  1 => "a"

julia> filter(p->isodd(p.first), d)
Dict{Int64, String} con 1 entrada:
  1 => "a"
```
