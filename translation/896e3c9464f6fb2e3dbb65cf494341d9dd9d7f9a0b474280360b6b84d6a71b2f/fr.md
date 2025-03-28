```
Stateful(itr)
```

Il existe plusieurs façons de penser à cet enveloppeur d'itérateur :

1. Il fournit un enveloppeur mutable autour d'un itérateur et de son état d'itération.
2. Il transforme une abstraction semblable à un itérateur en une abstraction semblable à un `Channel`.
3. C'est un itérateur qui se muta pour devenir son propre itérateur de reste chaque fois qu'un élément est produit.

`Stateful` fournit l'interface d'itérateur régulière. Comme d'autres itérateurs mutables (par exemple, [`Base.Channel`](@ref)), si l'itération est arrêtée prématurément (par exemple, par un [`break`](@ref) dans une boucle [`for`](@ref)), l'itération peut être reprise au même endroit en continuant à itérer sur le même objet itérateur (en revanche, un itérateur immuable redémarrerait depuis le début).

# Exemples

```jldoctest
julia> a = Iterators.Stateful("abcdef");

julia> isempty(a)
false

julia> popfirst!(a)
'a': ASCII/Unicode U+0061 (catégorie Ll : Lettre, minuscule)

julia> collect(Iterators.take(a, 3))
3-element Vector{Char}:
 'b': ASCII/Unicode U+0062 (catégorie Ll : Lettre, minuscule)
 'c': ASCII/Unicode U+0063 (catégorie Ll : Lettre, minuscule)
 'd': ASCII/Unicode U+0064 (catégorie Ll : Lettre, minuscule)

julia> collect(a)
2-element Vector{Char}:
 'e': ASCII/Unicode U+0065 (catégorie Ll : Lettre, minuscule)
 'f': ASCII/Unicode U+0066 (catégorie Ll : Lettre, minuscule)

julia> Iterators.reset!(a); popfirst!(a)
'a': ASCII/Unicode U+0061 (catégorie Ll : Lettre, minuscule)

julia> Iterators.reset!(a, "hello"); popfirst!(a)
'h': ASCII/Unicode U+0068 (catégorie Ll : Lettre, minuscule)
```

```jldoctest
julia> a = Iterators.Stateful([1,1,1,2,3,4]);

julia> for x in a; x == 1 || break; end

julia> peek(a)
3

julia> sum(a) # Somme des éléments restants
7
```
