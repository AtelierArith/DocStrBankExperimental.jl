```
log1p(x)
```

Logarithme naturel précis de `1+x`. Lance une [`DomainError`](@ref) pour les arguments [`Real`](@ref) inférieurs à -1.

# Exemples

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log1p(-0.5)
-0.6931471805599453

julia> log1p(0)
0.0

julia> log1p(-2)
ERROR: DomainError with -2.0:
log1p a été appelé avec un argument réel < -1 mais ne renverra un résultat complexe que s'il est appelé avec un argument complexe. Essayez log1p(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]
```
