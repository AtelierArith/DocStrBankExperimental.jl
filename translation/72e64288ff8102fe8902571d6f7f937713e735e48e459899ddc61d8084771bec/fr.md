```
pour outer
```

Réutilisez une variable locale existante pour l'itération dans une boucle `for`.

Voir la [section du manuel sur la portée des variables](@ref scope-of-variables) pour plus d'informations.

Voir aussi [`for`](@ref).

# Exemples

```jldoctest
julia> function f()
           i = 0
           for i = 1:3
               # vide
           end
           return i
       end;

julia> f()
0
```

```jldoctest
julia> function f()
           i = 0
           for outer i = 1:3
               # vide
           end
           return i
       end;

julia> f()
3
```

```jldoctest
julia> i = 0 # variable globale
       for outer i = 1:3
       end
ERREUR: syntaxe : aucune déclaration de variable locale externe n'existe pour "for outer"
[...]
```
