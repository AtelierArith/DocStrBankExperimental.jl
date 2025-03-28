```
log(x)
```

Calcule le logarithme naturel de `x`.

Lève une [`DomainError`](@ref) pour les arguments [`Real`](@ref) négatifs. Utilisez des arguments complexes pour obtenir des résultats complexes. A une coupure de branche le long de l'axe réel négatif, pour lequel `-0.0im` est considéré comme étant en dessous de l'axe.

Voir aussi [`ℯ`](@ref), [`log1p`](@ref), [`log2`](@ref), [`log10`](@ref).

# Exemples

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log(2)
0.6931471805599453

julia> log(-3)
ERROR: DomainError with -3.0:
log a été appelé avec un argument réel négatif mais ne renverra un résultat complexe que s'il est appelé avec un argument complexe. Essayez log(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]

julia> log(-3 + 0im)
1.0986122886681098 + 3.141592653589793im

julia> log(-3 - 0.0im)
1.0986122886681098 - 3.141592653589793im

julia> log.(exp.(-1:1))
3-element Vector{Float64}:
 -1.0
  0.0
  1.0
```
