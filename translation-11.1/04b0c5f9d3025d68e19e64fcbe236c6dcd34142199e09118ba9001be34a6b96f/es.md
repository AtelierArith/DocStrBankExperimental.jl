```
filter!(f, d::AbstractDict)
```

Actualiza `d`, eliminando elementos para los cuales `f` es `false`. La función `f` recibe pares `key=>value`.

# Ejemplos

```jldoctest
julia> d = Dict(1=>"a", 2=>"b", 3=>"c")
Dict{Int64, String} con 3 entradas:
  2 => "b"
  3 => "c"
  1 => "a"

julia> filter!(p->isodd(p.first), d)
Dict{Int64, String} con 2 entradas:
  3 => "c"
  1 => "a"
```
