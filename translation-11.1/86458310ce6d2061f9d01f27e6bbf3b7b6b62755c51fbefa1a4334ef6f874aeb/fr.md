```
==(x, y)
```

Opérateur d'égalité générique. Se rabat sur [`===`](@ref). Doit être implémenté pour tous les types ayant une notion d'égalité, basée sur la valeur abstraite qu'une instance représente. Par exemple, tous les types numériques sont comparés par valeur numérique, en ignorant le type. Les chaînes de caractères sont comparées comme des séquences de caractères, en ignorant l'encodage. Les collections du même type comparent généralement leurs ensembles de clés, et si celles-ci sont `==`, alors elles comparent les valeurs pour chacune de ces clés, retournant vrai si toutes ces paires sont `==`. D'autres propriétés ne sont généralement pas prises en compte (comme le type exact).

Cet opérateur suit la sémantique IEEE pour les nombres à virgule flottante : `0.0 == -0.0` et `NaN != NaN`.

Le résultat est de type `Bool`, sauf lorsque l'un des opérandes est [`missing`](@ref), auquel cas `missing` est retourné ([logique à trois valeurs](https://en.wikipedia.org/wiki/Three-valued_logic)). Les collections implémentent généralement une logique à trois valeurs semblable à [`all`](@ref), retournant missing si des opérandes contiennent des valeurs manquantes et que toutes les autres paires sont égales. Utilisez [`isequal`](@ref) ou [`===`](@ref) pour obtenir toujours un résultat de type `Bool`.

# Implémentation

Les nouveaux types numériques doivent implémenter cette fonction pour deux arguments du nouveau type, et gérer la comparaison avec d'autres types via des règles de promotion lorsque cela est possible.

[`isequal`](@ref) se rabat sur `==`, donc les nouvelles méthodes de `==` seront utilisées par le type [`Dict`](@ref) pour comparer les clés. Si votre type sera utilisé comme clé de dictionnaire, il doit donc également implémenter [`hash`](@ref).

Si un type définit `==`, [`isequal`](@ref) et [`isless`](@ref), alors il doit également implémenter [`<`](@ref) pour garantir la cohérence des comparaisons.
