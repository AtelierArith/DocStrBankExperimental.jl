```
@generated f
```

`@generated` est utilisé pour annoter une fonction qui sera générée. Dans le corps de la fonction générée, seuls les types des arguments peuvent être lus (pas les valeurs). La fonction renvoie une expression citée évaluée lorsque la fonction est appelée. Le macro `@generated` ne doit pas être utilisé sur des fonctions modifiant l'espace global ou dépendant d'éléments mutables.

Voir [Metaprogramming](@ref) pour plus de détails.

# Exemples

```jldoctest
julia> @generated function bar(x)
           if x <: Integer
               return :(x ^ 2)
           else
               return :(x)
           end
       end
bar (generic function with 1 method)

julia> bar(4)
16

julia> bar("baz")
"baz"
```
