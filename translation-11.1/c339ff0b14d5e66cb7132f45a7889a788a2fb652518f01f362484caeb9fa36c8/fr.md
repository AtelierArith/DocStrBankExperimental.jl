```
Iterators.filter(flt, itr)
```

Étant donné une fonction prédicat `flt` et un objet itérable `itr`, renvoie un objet itérable qui, lors de l'itération, produit les éléments `x` de `itr` qui satisfont `flt(x)`. L'ordre de l'itérateur original est préservé.

Cette fonction est *paresseuse* ; c'est-à-dire qu'elle garantit de renvoyer en $Θ(1)$ temps et d'utiliser $Θ(1)$ espace supplémentaire, et `flt` ne sera pas appelé par une invocation de `filter`. Des appels à `flt` seront effectués lors de l'itération sur l'objet itérable retourné. Ces appels ne sont pas mis en cache et des appels répétés seront effectués lors de la réitération.

!!! avertissement
    Des transformations *paresseuses* ultérieures sur l'itérateur retourné par `filter`, telles que celles effectuées par `Iterators.reverse` ou `cycle`, retarderont également les appels à `flt` jusqu'à la collecte ou l'itération sur l'objet itérable retourné. Si le prédicat de filtrage est non déterministe ou si ses valeurs de retour dépendent de l'ordre d'itération sur les éléments de `itr`, la composition avec des transformations paresseuses peut entraîner un comportement surprenant. Si cela est indésirable, assurez-vous que `flt` est une fonction pure ou collectez des itérateurs `filter` intermédiaires avant d'autres transformations.


Voir [`Base.filter`](@ref) pour une implémentation avide du filtrage pour les tableaux.

# Exemples

```jldoctest
julia> f = Iterators.filter(isodd, [1, 2, 3, 4, 5])
Base.Iterators.Filter{typeof(isodd), Vector{Int64}}(isodd, [1, 2, 3, 4, 5])

julia> foreach(println, f)
1
3
5

julia> [x for x in [1, 2, 3, 4, 5] if isodd(x)]  # collecte un générateur sur Iterators.filter
3-element Vector{Int64}:
 1
 3
 5
```
