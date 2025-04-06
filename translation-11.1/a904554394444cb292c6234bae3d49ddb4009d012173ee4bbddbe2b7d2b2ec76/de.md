```
rand!([rng=default_rng()], A, [S=eltype(A)])
```

Füllen Sie das Array `A` mit zufälligen Werten. Wenn `S` angegeben ist (`S` kann ein Typ oder eine Sammlung sein, siehe [`rand`](@ref) für Details), werden die Werte zufällig aus `S` ausgewählt. Dies ist äquivalent zu `copyto!(A, rand(rng, S, size(A)))`, jedoch ohne ein neues Array zuzuweisen.

# Beispiele

```jldoctest
julia> rand!(Xoshiro(123), zeros(5))
5-element Vector{Float64}:
 0.521213795535383
 0.5868067574533484
 0.8908786980927811
 0.19090669902576285
 0.5256623915420473
```
