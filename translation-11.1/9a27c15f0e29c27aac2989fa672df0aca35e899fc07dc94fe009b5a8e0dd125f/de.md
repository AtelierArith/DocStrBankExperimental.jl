```
log1p(x)
```

Genauer natürlicher Logarithmus von `1+x`. Wirft [`DomainError`](@ref) für [`Real`](@ref) Argumente kleiner als -1.

# Beispiele

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log1p(-0.5)
-0.6931471805599453

julia> log1p(0)
0.0

julia> log1p(-2)
ERROR: DomainError mit -2.0:
log1p wurde mit einem reellen Argument < -1 aufgerufen, gibt aber nur ein komplexes Ergebnis zurück, wenn es mit einem komplexen Argument aufgerufen wird. Versuchen Sie log1p(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]
```
