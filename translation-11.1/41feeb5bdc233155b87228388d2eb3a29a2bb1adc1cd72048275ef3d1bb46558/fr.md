```
Iterators.reverse(itr)
```

Étant donné un itérateur `itr`, alors `reverse(itr)` est un itérateur sur la même collection mais dans l'ordre inverse. Cet itérateur est "paresseux" en ce sens qu'il ne fait pas de copie de la collection pour l'inverser ; voir [`Base.reverse`](@ref) pour une implémentation avide.

(Par défaut, cela renvoie un objet `Iterators.Reverse` enveloppant `itr`, qui est itérable si les méthodes [`iterate`](@ref) correspondantes sont définies, mais certains types `itr` peuvent implémenter des comportements `Iterators.reverse` plus spécialisés.)

Tous les types d'itérateurs `T` ne prennent pas en charge l'itération dans l'ordre inverse. Si `T` ne le fait pas, alors itérer sur `Iterators.reverse(itr::T)` lancera une [`MethodError`](@ref) en raison des méthodes `iterate` manquantes pour `Iterators.Reverse{T}`. (Pour implémenter ces méthodes, l'itérateur original `itr::T` peut être obtenu à partir d'un objet `r::Iterators.Reverse{T}` par `r.itr` ; plus généralement, on peut utiliser `Iterators.reverse(r)`.)

# Exemples

```jldoctest
julia> foreach(println, Iterators.reverse(1:5))
5
4
3
2
1
```
