```
log10(x)
```

Berechne den Logarithmus von `x` zur Basis 10. Wirft [`DomainError`](@ref) für negative [`Real`](@ref) Argumente.

# Beispiele

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log10(100)
2.0

julia> log10(2)
0.3010299956639812

julia> log10(-2)
ERROR: DomainError mit -2.0:
log10 wurde mit einem negativen reellen Argument aufgerufen, gibt aber nur ein komplexes Ergebnis zurück, wenn es mit einem komplexen Argument aufgerufen wird. Versuche log10(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(f::Symbol, x::Float64) at ./math.jl:31
[...]
```
