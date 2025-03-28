```
log1p(x)
```

Logaritmo natural preciso de `1+x`. Lanza [`DomainError`](@ref) para argumentos [`Real`](@ref) menores que -1.

# Ejemplos

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log1p(-0.5)
-0.6931471805599453

julia> log1p(0)
0.0

julia> log1p(-2)
ERROR: DomainError con -2.0:
log1p fue llamado con un argumento real < -1 pero solo devolverá un resultado complejo si se llama con un argumento complejo. Intenta log1p(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]
```
