```
randn!([rng=default_rng()], A::AbstractArray) -> A
```

Remplit le tableau `A` avec des nombres aléatoires distribués normalement (moyenne 0, écart type 1). Voir aussi la fonction [`rand`](@ref).

# Exemples

```jldoctest
julia> randn!(Xoshiro(123), zeros(5))
5-element Vector{Float64}:
 -0.6457306721039767
 -1.4632513788889214
 -1.6236037455860806
 -0.21766510678354617
  0.4922456865251828
```
