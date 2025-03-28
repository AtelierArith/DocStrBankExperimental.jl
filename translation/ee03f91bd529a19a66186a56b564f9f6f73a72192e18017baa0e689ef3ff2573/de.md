```
sqrt(x)
```

Gibt $\sqrt{x}$ zurück.

Wirft [`DomainError`](@ref) für negative [`Real`](@ref) Argumente. Verwenden Sie stattdessen komplexe negative Argumente. Beachten Sie, dass `sqrt` einen Zweigschnitt entlang der negativen reellen Achse hat.

Der Präfixoperator `√` ist äquivalent zu `sqrt`.

Siehe auch: [`hypot`](@ref).

# Beispiele

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> sqrt(big(81))
9.0

julia> sqrt(big(-81))
ERROR: DomainError mit -81.0:
NaN-Ergebnis für nicht-NaN-Eingabe.
Stacktrace:
 [1] sqrt(::BigFloat) at ./mpfr.jl:501
[...]

julia> sqrt(big(complex(-81)))
0.0 + 9.0im

julia> sqrt(-81 - 0.0im)  # -0.0im liegt unter dem Zweigschnitt
0.0 - 9.0im

julia> .√(1:4)
4-element Vector{Float64}:
 1.0
 1.4142135623730951
 1.7320508075688772
 2.0
```
