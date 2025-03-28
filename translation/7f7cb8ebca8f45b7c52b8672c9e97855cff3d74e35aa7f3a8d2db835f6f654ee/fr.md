```
@. expr
```

Convertir chaque appel de fonction ou opérateur dans `expr` en un "appel avec point" (par exemple, convertir `f(x)` en `f.(x)`), et convertir chaque affectation dans `expr` en une "affectation avec point" (par exemple, convertir `+=` en `.+=`).

Si vous souhaitez *éviter* d'ajouter des points pour des appels de fonction sélectionnés dans `expr`, insérez ces appels de fonction avec `$`. Par exemple, `@. sqrt(abs($sort(x)))` est équivalent à `sqrt.(abs.(sort(x)))` (pas de point pour `sort`).

(`@.` est équivalent à un appel à `@__dot__`.)

# Exemples

```jldoctest
julia> x = 1.0:3.0; y = similar(x);

julia> @. y = x + 3 * sin(x)
3-element Vector{Float64}:
 3.5244129544236893
 4.727892280477045
 3.4233600241796016
```
