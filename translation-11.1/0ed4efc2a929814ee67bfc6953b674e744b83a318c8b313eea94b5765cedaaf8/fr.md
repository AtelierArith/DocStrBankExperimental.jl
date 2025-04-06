```
map!(f, values(dict::AbstractDict))
```

Modifie `dict` en transformant chaque valeur de `val` en `f(val)`. Notez que le type de `dict` ne peut pas être changé : si `f(val)` n'est pas une instance du type de valeur de `dict`, alors il sera converti en type de valeur si possible et sinon, une erreur sera levée.

!!! compat "Julia 1.2"
    `map!(f, values(dict::AbstractDict))` nécessite Julia 1.2 ou une version ultérieure.


# Exemples

```jldoctest
julia> d = Dict(:a => 1, :b => 2)
Dict{Symbol, Int64} avec 2 entrées :
  :a => 1
  :b => 2

julia> map!(v -> v-1, values(d))
ValueIterator pour un Dict{Symbol, Int64} avec 2 entrées. Valeurs :
  0
  1
```
