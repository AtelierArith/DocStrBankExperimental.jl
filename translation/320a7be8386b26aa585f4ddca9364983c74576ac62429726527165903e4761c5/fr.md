```
fetch(c::Channel)
```

Attend et retourne (sans supprimer) le premier élément disponible du `Channel`. Remarque : `fetch` n'est pas pris en charge sur un `Channel` non tamponné (taille 0).

# Exemples

Channel tamponné :

```jldoctest
julia> c = Channel(3) do ch
           foreach(i -> put!(ch, i), 1:3)
       end;

julia> fetch(c)
1

julia> collect(c)  # l'élément n'est pas supprimé
3-element Vector{Any}:
 1
 2
 3
```
