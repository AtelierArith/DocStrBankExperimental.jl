```
length(s::AbstractString) -> Int
length(s::AbstractString, i::Integer, j::Integer) -> Int
```

Retourne le nombre de caractères dans la chaîne `s` des indices `i` à `j`.

Cela est calculé comme le nombre d'indices d'unités de code de `i` à `j` qui sont des indices de caractères valides. Avec un seul argument de chaîne, cela calcule le nombre de caractères dans l'ensemble de la chaîne. Avec les arguments `i` et `j`, cela calcule le nombre d'indices entre `i` et `j` inclus qui sont des indices valides dans la chaîne `s`. En plus des valeurs dans les limites, `i` peut prendre la valeur hors limites `ncodeunits(s) + 1` et `j` peut prendre la valeur hors limites `0`.

!!! note
    La complexité temporelle de cette opération est généralement linéaire. C'est-à-dire qu'elle prendra un temps proportionnel au nombre d'octets ou de caractères dans la chaîne car elle compte la valeur à la volée. Cela contraste avec la méthode pour les tableaux, qui est une opération en temps constant.


Voir aussi [`isvalid`](@ref), [`ncodeunits`](@ref), [`lastindex`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref).

# Exemples

```jldoctest
julia> length("jμΛIα")
5
```
