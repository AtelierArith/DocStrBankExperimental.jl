```
log10(x)
```

Calcula el logaritmo de `x` en base 10. Lanza [`DomainError`](@ref) para argumentos [`Real`](@ref) negativos.

# Ejemplos

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log10(100)
2.0

julia> log10(2)
0.3010299956639812

julia> log10(-2)
ERROR: DomainError con -2.0:
log10 fue llamado con un argumento real negativo pero solo devolverá un resultado complejo si se llama con un argumento complejo. Intenta log10(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(f::Symbol, x::Float64) at ./math.jl:31
[...]
```
