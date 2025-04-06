```
log2(x)
```

Berechnet den Logarithmus von `x` zur Basis 2. Wirft [`DomainError`](@ref) für negative [`Real`](@ref) Argumente.

Siehe auch: [`exp2`](@ref), [`ldexp`](@ref), [`ispow2`](@ref).

# Beispiele

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log2(4)
2.0

julia> log2(10)
3.321928094887362

julia> log2(-2)
ERROR: DomainError mit -2.0:
log2 wurde mit einem negativen reellen Argument aufgerufen, gibt aber nur ein komplexes Ergebnis zurück, wenn es mit einem komplexen Argument aufgerufen wird. Versuchen Sie log2(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(f::Symbol, x::Float64) at ./math.jl:31
[...]

julia> log2.(2.0 .^ (-1:1))
3-element Vector{Float64}:
 -1.0
  0.0
  1.0
```
