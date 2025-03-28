```
@show exs...
```

Gibt einen oder mehrere Ausdrücke und deren Ergebnisse an `stdout` aus und gibt das letzte Ergebnis zurück.

Siehe auch: [`show`](@ref), [`@info`](@ref man-logging), [`println`](@ref).

# Beispiele

```jldoctest
julia> x = @show 1+2
1 + 2 = 3
3

julia> @show x^2 x/2;
x ^ 2 = 9
x / 2 = 1.5
```
