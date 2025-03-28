```
log(x)
```

Calcula el logaritmo natural de `x`.

Lanza [`DomainError`](@ref) para argumentos [`Real`](@ref) negativos. Usa argumentos complejos para obtener resultados complejos. Tiene un corte de rama a lo largo del eje real negativo, para el cual `-0.0im` se considera por debajo del eje.

Véase también [`ℯ`](@ref), [`log1p`](@ref), [`log2`](@ref), [`log10`](@ref).

# Ejemplos

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log(2)
0.6931471805599453

julia> log(-3)
ERROR: DomainError with -3.0:
log fue llamado con un argumento real negativo pero solo devolverá un resultado complejo si se llama con un argumento complejo. Intenta log(Complex(x)).
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]

julia> log(-3 + 0im)
1.0986122886681098 + 3.141592653589793im

julia> log(-3 - 0.0im)
1.0986122886681098 - 3.141592653589793im

julia> log.(exp.(-1:1))
Vector{Float64} de 3 elementos:
 -1.0
  0.0
  1.0
```
