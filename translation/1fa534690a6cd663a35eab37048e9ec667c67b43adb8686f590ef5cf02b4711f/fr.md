```
log2(x)
```

Calcule le logarithme de `x` en base 2. Lance une [`DomainError`](@ref) pour les arguments [`Real`](@ref) négatifs.

Voir aussi : [`exp2`](@ref), [`ldexp`](@ref), [`ispow2`](@ref).

# Exemples

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log2(4)
2.0

julia> log2(10)
3.321928094887362

julia> log2(-2)
ERROR: DomainError with -2.0:
log2 a été appelé avec un argument réel négatif mais ne renverra qu'un résultat complexe s'il est appelé avec un argument complexe. Essayez log2(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(f::Symbol, x::Float64) at ./math.jl:31
[...]

julia> log2.(2.0 .^ (-1:1))
3-element Vector{Float64}:
 -1.0
  0.0
  1.0
```
