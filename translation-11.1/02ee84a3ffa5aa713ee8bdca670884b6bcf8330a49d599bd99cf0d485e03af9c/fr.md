```
log10(x)
```

Calcule le logarithme de `x` en base 10. Lance une [`DomainError`](@ref) pour les arguments [`Real`](@ref) négatifs.

# Exemples

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log10(100)
2.0

julia> log10(2)
0.3010299956639812

julia> log10(-2)
ERROR: DomainError with -2.0:
log10 a été appelé avec un argument réel négatif mais ne renverra un résultat complexe que s'il est appelé avec un argument complexe. Essayez log10(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(f::Symbol, x::Float64) at ./math.jl:31
[...]
```
