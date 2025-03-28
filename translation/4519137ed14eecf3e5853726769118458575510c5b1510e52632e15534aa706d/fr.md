```
isequal(x, y) -> Bool
```

Semblable à [`==`](@ref), sauf pour le traitement des nombres à virgule flottante et des valeurs manquantes. `isequal` considère toutes les valeurs `NaN` à virgule flottante comme égales entre elles, considère `-0.0` comme inégal à `0.0`, et [`missing`](@ref) comme égal à `missing`. Renvoie toujours une valeur de type `Bool`.

`isequal` est une relation d'équivalence - elle est réflexive (`===` implique `isequal`), symétrique (`isequal(a, b)` implique `isequal(b, a)`) et transitive (`isequal(a, b)` et `isequal(b, c)` implique `isequal(a, c)`).

# Implémentation

L'implémentation par défaut de `isequal` appelle `==`, donc un type qui n'implique pas de valeurs à virgule flottante n'a généralement besoin de définir que `==`.

`isequal` est la fonction de comparaison utilisée par les tables de hachage (`Dict`). `isequal(x,y)` doit impliquer que `hash(x) == hash(y)`.

Cela signifie généralement que les types pour lesquels une méthode personnalisée `==` ou `isequal` existe doivent implémenter une méthode [`hash`](@ref) correspondante (et vice versa). Les collections implémentent généralement `isequal` en appelant `isequal` de manière récursive sur tous les contenus.

De plus, `isequal` est lié à [`isless`](@ref), et ils travaillent ensemble pour définir un ordre total fixe, où exactement l'un de `isequal(x, y)`, `isless(x, y)`, ou `isless(y, x)` doit être `true` (et les deux autres `false`).

Les types scalaires n'ont généralement pas besoin d'implémenter `isequal` séparément de `==`, à moins qu'ils ne représentent des nombres à virgule flottante susceptibles d'une implémentation plus efficace que celle fournie comme solution générique (basée sur `isnan`, `signbit`, et `==`).

# Exemples

```jldoctest
julia> isequal([1., NaN], [1., NaN])
true

julia> [1., NaN] == [1., NaN]
false

julia> 0.0 == -0.0
true

julia> isequal(0.0, -0.0)
false

julia> missing == missing
missing

julia> isequal(missing, missing)
true
```
