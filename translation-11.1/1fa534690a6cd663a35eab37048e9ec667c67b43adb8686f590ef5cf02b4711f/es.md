```
log2(x)
```

Calcula el logaritmo de `x` en base 2. Lanza [`DomainError`](@ref) para argumentos [`Real`](@ref) negativos.

Véase también: [`exp2`](@ref), [`ldexp`](@ref), [`ispow2`](@ref).

# Ejemplos

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log2(4)
2.0

julia> log2(10)
3.321928094887362

julia> log2(-2)
ERROR: DomainError con -2.0:
log2 fue llamado con un argumento real negativo pero solo devolverá un resultado complejo si se llama con un argumento complejo. Intenta log2(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(f::Symbol, x::Float64) at ./math.jl:31
[...]

julia> log2.(2.0 .^ (-1:1))
Vector{Float64} de 3 elementos:
 -1.0
  0.0
  1.0
```
