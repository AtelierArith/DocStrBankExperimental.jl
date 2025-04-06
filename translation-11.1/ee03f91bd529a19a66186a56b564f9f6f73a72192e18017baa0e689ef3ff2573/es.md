```
sqrt(x)
```

Devuelve $\sqrt{x}$.

Lanza [`DomainError`](@ref) para argumentos [`Real`](@ref) negativos. Usa argumentos negativos complejos en su lugar. Ten en cuenta que `sqrt` tiene un corte de rama a lo largo del eje real negativo.

El operador prefijo `√` es equivalente a `sqrt`.

Véase también: [`hypot`](@ref).

# Ejemplos

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> sqrt(big(81))
9.0

julia> sqrt(big(-81))
ERROR: DomainError con -81.0:
Resultado NaN para entrada no-NaN.
Stacktrace:
 [1] sqrt(::BigFloat) at ./mpfr.jl:501
[...]

julia> sqrt(big(complex(-81)))
0.0 + 9.0im

julia> sqrt(-81 - 0.0im)  # -0.0im está por debajo del corte de rama
0.0 - 9.0im

julia> .√(1:4)
Vector de 4 elementos{Float64}:
 1.0
 1.4142135623730951
 1.7320508075688772
 2.0
```
