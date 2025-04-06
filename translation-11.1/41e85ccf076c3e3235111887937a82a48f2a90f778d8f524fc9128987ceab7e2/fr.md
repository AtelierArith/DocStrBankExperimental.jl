```
merge(d::AbstractDict, others::AbstractDict...)
```

Construit une collection fusionnée à partir des collections données. Si nécessaire, les types de la collection résultante seront promus pour s'adapter aux types des collections fusionnées. Si la même clé est présente dans une autre collection, la valeur pour cette clé sera celle qu'elle a dans la dernière collection listée. Voir aussi [`mergewith`](@ref) pour un traitement personnalisé des valeurs avec la même clé.

# Exemples

```jldoctest
julia> a = Dict("foo" => 0.0, "bar" => 42.0)
Dict{String, Float64} avec 2 entrées :
  "bar" => 42.0
  "foo" => 0.0

julia> b = Dict("baz" => 17, "bar" => 4711)
Dict{String, Int64} avec 2 entrées :
  "bar" => 4711
  "baz" => 17

julia> merge(a, b)
Dict{String, Float64} avec 3 entrées :
  "bar" => 4711.0
  "baz" => 17.0
  "foo" => 0.0

julia> merge(b, a)
Dict{String, Float64} avec 3 entrées :
  "bar" => 42.0
  "baz" => 17.0
  "foo" => 0.0
```
