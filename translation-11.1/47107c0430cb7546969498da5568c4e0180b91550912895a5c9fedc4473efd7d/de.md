```
log(x)
```

Berechnet den natürlichen Logarithmus von `x`.

Wirft [`DomainError`](@ref) für negative [`Real`](@ref) Argumente. Verwenden Sie komplexe Argumente, um komplexe Ergebnisse zu erhalten. Hat einen Astschnitt entlang der negativen reellen Achse, für den `-0.0im` als unterhalb der Achse betrachtet wird.

Siehe auch [`ℯ`](@ref), [`log1p`](@ref), [`log2`](@ref), [`log10`](@ref).

# Beispiele

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log(2)
0.6931471805599453

julia> log(-3)
ERROR: DomainError with -3.0:
log wurde mit einem negativen reellen Argument aufgerufen, gibt jedoch nur ein komplexes Ergebnis zurück, wenn es mit einem komplexen Argument aufgerufen wird. Versuchen Sie log(Complex(x)).
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
