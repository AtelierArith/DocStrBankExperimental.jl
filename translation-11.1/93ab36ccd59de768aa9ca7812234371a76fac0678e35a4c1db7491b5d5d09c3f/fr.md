```
isapprox(x, y; atol::Real=0, rtol::Real=atol>0 ? 0 : √eps, nans::Bool=false[, norm::Function])
```

Comparaison d'égalité inexacte. Deux nombres sont considérés égaux si leur distance relative *ou* leur distance absolue est dans les limites de tolérance : `isapprox` renvoie `true` si `norm(x-y) <= max(atol, rtol*max(norm(x), norm(y)))`. La valeur par défaut de `atol` (tolérance absolue) est zéro et la valeur par défaut de `rtol` (tolérance relative) dépend des types de `x` et `y`. L'argument clé `nans` détermine si les valeurs NaN sont considérées comme égales (par défaut, faux).

Pour les valeurs flottantes réelles ou complexes, si un `atol > 0` n'est pas spécifié, `rtol` par défaut est la racine carrée de [`eps`](@ref) du type de `x` ou `y`, selon celui qui est le plus grand (le moins précis). Cela correspond à exiger l'égalité d'environ la moitié des chiffres significatifs. Sinon, par exemple pour des arguments entiers ou si un `atol > 0` est fourni, `rtol` par défaut est zéro.

L'argument clé `norm` par défaut est `abs` pour les numériques `(x,y)` et `LinearAlgebra.norm` pour les tableaux (où un choix alternatif de `norm` est parfois utile). Lorsque `x` et `y` sont des tableaux, si `norm(x-y)` n'est pas fini (c'est-à-dire `±Inf` ou `NaN`), la comparaison revient à vérifier si tous les éléments de `x` et `y` sont approximativement égaux composant par composant.

L'opérateur binaire `≈` est équivalent à `isapprox` avec les arguments par défaut, et `x ≉ y` est équivalent à `!isapprox(x,y)`.

Notez que `x ≈ 0` (c'est-à-dire, comparer à zéro avec les tolérances par défaut) est équivalent à `x == 0` puisque la valeur par défaut de `atol` est `0`. Dans de tels cas, vous devriez soit fournir un `atol` approprié (ou utiliser `norm(x) ≤ atol`) soit réorganiser votre code (par exemple, utiliser `x ≈ y` plutôt que `x - y ≈ 0`). Il n'est pas possible de choisir automatiquement un `atol` non nul car cela dépend de l'échelle globale (les "unités") de votre problème : par exemple, dans `x - y ≈ 0`, `atol=1e-9` est une tolérance ridiculement petite si `x` est le [rayon de la Terre](https://en.wikipedia.org/wiki/Earth_radius) en mètres, mais une tolérance ridiculement grande si `x` est le [rayon d'un atome d'hydrogène](https://en.wikipedia.org/wiki/Bohr_radius) en mètres.

!!! compat "Julia 1.6"
    Passer l'argument clé `norm` lors de la comparaison d'arguments numériques (non-tableaux) nécessite Julia 1.6 ou une version ultérieure.


# Exemples

```jldoctest
julia> isapprox(0.1, 0.15; atol=0.05)
true

julia> isapprox(0.1, 0.15; rtol=0.34)
true

julia> isapprox(0.1, 0.15; rtol=0.33)
false

julia> 0.1 + 1e-10 ≈ 0.1
true

julia> 1e-10 ≈ 0
false

julia> isapprox(1e-10, 0, atol=1e-8)
true

julia> isapprox([10.0^9, 1.0], [10.0^9, 2.0]) # utilisant `norm`
true
```
