```
@nref N A indexexpr
```

Générer des expressions comme `A[i_1, i_2, ...]`. `indexexpr` peut être soit un préfixe de symbole d'itération, soit une expression de fonction anonyme.

# Exemples

```jldoctest
julia> @macroexpand Base.Cartesian.@nref 3 A i
:(A[i_1, i_2, i_3])
```
