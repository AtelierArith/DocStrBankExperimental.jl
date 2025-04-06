```
map!(f, values(dict::AbstractDict))
```

Modifica `dict` transformando cada valor de `val` a `f(val)`. Ten en cuenta que el tipo de `dict` no puede ser cambiado: si `f(val)` no es una instancia del tipo de valor de `dict`, entonces se convertirá al tipo de valor si es posible y, de lo contrario, se generará un error.

!!! compat "Julia 1.2"
    `map!(f, values(dict::AbstractDict))` requiere Julia 1.2 o posterior.


# Ejemplos

```jldoctest
julia> d = Dict(:a => 1, :b => 2)
Dict{Symbol, Int64} con 2 entradas:
  :a => 1
  :b => 2

julia> map!(v -> v-1, values(d))
ValueIterator para un Dict{Symbol, Int64} con 2 entradas. Valores:
  0
  1
```
