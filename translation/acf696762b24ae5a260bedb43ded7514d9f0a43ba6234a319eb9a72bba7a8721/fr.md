```
mergewith(combine, d::AbstractDict, others::AbstractDict...)
mergewith(combine)
merge(combine, d::AbstractDict, others::AbstractDict...)
```

Construisez une collection fusionnée à partir des collections données. Si nécessaire, les types de la collection résultante seront promus pour s'adapter aux types des collections fusionnées. Les valeurs ayant la même clé seront combinées à l'aide de la fonction de combinaison. La forme curried `mergewith(combine)` renvoie la fonction `(args...) -> mergewith(combine, args...)`.

La méthode `merge(combine::Union{Function,Type}, args...)` en tant qu'alias de `mergewith(combine, args...)` est toujours disponible pour la compatibilité ascendante.

!!! compat "Julia 1.5"
    `mergewith` nécessite Julia 1.5 ou une version ultérieure.


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

julia> mergewith(+, a, b)
Dict{String, Float64} avec 3 entrées :
  "bar" => 4753.0
  "baz" => 17.0
  "foo" => 0.0

julia> ans == mergewith(+)(a, b)
true
```
