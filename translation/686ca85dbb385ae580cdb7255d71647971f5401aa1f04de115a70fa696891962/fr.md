```
Base.isambiguous(m1, m2; ambiguous_bottom=false) -> Bool
```

Détermine si deux méthodes `m1` et `m2` peuvent être ambiguës pour une certaine signature d'appel. Ce test est effectué dans le contexte d'autres méthodes de la même fonction ; isolément, `m1` et `m2` pourraient être ambiguës, mais si une troisième méthode résolvant l'ambiguïté a été définie, cela retourne `false`. Alternativement, isolément `m1` et `m2` pourraient être ordonnées, mais si une troisième méthode ne peut pas être triée avec elles, elles peuvent causer une ambiguïté ensemble.

Pour les types paramétriques, l'argument clé `ambiguous_bottom` contrôle si `Union{}` compte comme une intersection ambiguë de paramètres de type – lorsque `true`, il est considéré comme ambigu, lorsque `false`, il ne l'est pas.

# Exemples

```jldoctest
julia> foo(x::Complex{<:Integer}) = 1
foo (generic function with 1 method)

julia> foo(x::Complex{<:Rational}) = 2
foo (generic function with 2 methods)

julia> m1, m2 = collect(methods(foo));

julia> typeintersect(m1.sig, m2.sig)
Tuple{typeof(foo), Complex{Union{}}}

julia> Base.isambiguous(m1, m2, ambiguous_bottom=true)
true

julia> Base.isambiguous(m1, m2, ambiguous_bottom=false)
false
```
