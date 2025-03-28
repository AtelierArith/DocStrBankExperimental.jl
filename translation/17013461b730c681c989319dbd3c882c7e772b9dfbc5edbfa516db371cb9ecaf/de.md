```
randn!([rng=default_rng()], A::AbstractArray) -> A
```

Füllt das Array `A` mit normalverteilten (Mittelwert 0, Standardabweichung 1) Zufallszahlen. Siehe auch die [`rand`](@ref) Funktion.

# Beispiele

```jldoctest
julia> randn!(Xoshiro(123), zeros(5))
5-element Vector{Float64}:
 -0.6457306721039767
 -1.4632513788889214
 -1.6236037455860806
 -0.21766510678354617
  0.4922456865251828
```
