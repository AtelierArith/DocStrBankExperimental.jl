```
PartialQuickSort{T <: Union{Integer,OrdinalRange}}
```

Indiquez qu'une fonction de tri doit utiliser l'algorithme de tri rapide partiel. `PartialQuickSort(k)` est semblable à `QuickSort`, mais n'est requis que pour trouver et trier les éléments qui se retrouveraient dans `v[k]` si `v` était entièrement trié.

Caractéristiques :

  * *non stable* : ne préserve pas l'ordre des éléments qui se comparent comme égaux (par exemple, "a" et "A" dans un tri de lettres qui ignore la casse).
  * *en place* en mémoire.
  * *diviser pour régner* : stratégie de tri similaire à [`MergeSort`](@ref).

Notez que `PartialQuickSort(k)` ne trie pas nécessairement l'ensemble du tableau. Par exemple,

```jldoctest
julia> x = rand(100);

julia> k = 50:100;

julia> s1 = sort(x; alg=QuickSort);

julia> s2 = sort(x; alg=PartialQuickSort(k));

julia> map(issorted, (s1, s2))
(true, false)

julia> map(x->issorted(x[k]), (s1, s2))
(true, true)

julia> s1[k] == s2[k]
true
```
