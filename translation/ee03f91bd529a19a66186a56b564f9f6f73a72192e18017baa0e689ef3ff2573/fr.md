```
sqrt(x)
```

Retourne $\sqrt{x}$.

Lève une [`DomainError`](@ref) pour les arguments [`Real`](@ref) négatifs. Utilisez plutôt des arguments complexes négatifs. Notez que `sqrt` a une coupure de branche le long de l'axe réel négatif.

L'opérateur préfixe `√` est équivalent à `sqrt`.

Voir aussi : [`hypot`](@ref).

# Exemples

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> sqrt(big(81))
9.0

julia> sqrt(big(-81))
ERROR: DomainError with -81.0:
NaN result for non-NaN input.
Stacktrace:
 [1] sqrt(::BigFloat) at ./mpfr.jl:501
[...]

julia> sqrt(big(complex(-81)))
0.0 + 9.0im

julia> sqrt(-81 - 0.0im)  # -0.0im est en dessous de la coupure de branche
0.0 - 9.0im

julia> .√(1:4)
4-element Vector{Float64}:
 1.0
 1.4142135623730951
 1.7320508075688772
 2.0
```
