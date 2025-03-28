```
eigmax(A; permute::Bool=true, scale::Bool=true)
```

Devuelve el mayor valor propio de `A`. La opción `permute=true` permuta la matriz para acercarse a una forma triangular superior, y `scale=true` escala la matriz por sus elementos diagonales para hacer que las filas y columnas sean más iguales en norma. Ten en cuenta que si los valores propios de `A` son complejos, este método fallará, ya que los números complejos no se pueden ordenar.

# Ejemplos

```jldoctest
julia> A = [0 im; -im 0]
2×2 Matrix{Complex{Int64}}:
 0+0im  0+1im
 0-1im  0+0im

julia> eigmax(A)
1.0

julia> A = [0 im; -1 0]
2×2 Matrix{Complex{Int64}}:
  0+0im  0+1im
 -1+0im  0+0im

julia> eigmax(A)
ERROR: DomainError with Complex{Int64}[0+0im 0+1im; -1+0im 0+0im]:
`A` no puede tener valores propios complejos.
Stacktrace:
[...]
```
