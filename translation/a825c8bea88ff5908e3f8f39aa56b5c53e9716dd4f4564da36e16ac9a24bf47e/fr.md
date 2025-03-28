```
pour
```

`pour` les boucles évaluent à plusieurs reprises un bloc d'instructions tout en itérant sur une séquence de valeurs.

La variable d'itération est toujours une nouvelle variable, même si une variable du même nom existe dans la portée englobante. Utilisez [`outer`](@ref) pour réutiliser une variable locale existante pour l'itération.

# Exemples

```jldoctest
julia> pour i dans [1, 4, 0]
           println(i)
       fin
1
4
0
```
