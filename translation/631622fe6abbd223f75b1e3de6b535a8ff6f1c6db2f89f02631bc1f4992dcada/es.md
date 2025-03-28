```
replace(new::Union{Function, Type}, A; [count::Integer])
```

Devuelve una copia de `A` donde cada valor `x` en `A` es reemplazado por `new(x)`. Si se especifica `count`, entonces reemplaza como máximo `count` valores en total (los reemplazos se definen como `new(x) !== x`).

!!! compat "Julia 1.7"
    Se requiere la versión 1.7 para reemplazar elementos de un `Tuple`.


# Ejemplos

```jldoctest
julia> replace(x -> isodd(x) ? 2x : x, [1, 2, 3, 4])
4-element Vector{Int64}:
 2
 2
 6
 4

julia> replace(Dict(1=>2, 3=>4)) do kv
           first(kv) < 3 ? first(kv)=>3 : kv
       end
Dict{Int64, Int64} with 2 entries:
  3 => 4
  1 => 3
```
