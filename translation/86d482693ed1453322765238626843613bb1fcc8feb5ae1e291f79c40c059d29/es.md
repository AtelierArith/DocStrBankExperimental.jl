```
Hermitiano(A::AbstractMatrix, uplo::Symbol=:U)
```

Construye una vista `Hermitiano` del triángulo superior (si `uplo = :U`) o inferior (si `uplo = :L`) de la matriz `A`.

Para calcular la parte hermitiana de `A`, usa [`hermitianpart`](@ref).

# Ejemplos

```jldoctest
julia> A = [1 2+2im 3-3im; 4 5 6-6im; 7 8+8im 9]
3×3 Matrix{Complex{Int64}}:
 1+0im  2+2im  3-3im
 4+0im  5+0im  6-6im
 7+0im  8+8im  9+0im

julia> Hupper = Hermitiano(A)
3×3 Hermitiano{Complex{Int64}, Matrix{Complex{Int64}}}:
 1+0im  2+2im  3-3im
 2-2im  5+0im  6-6im
 3+3im  6+6im  9+0im

julia> Hlower = Hermitiano(A, :L)
3×3 Hermitiano{Complex{Int64}, Matrix{Complex{Int64}}}:
 1+0im  4+0im  7+0im
 4+0im  5+0im  8-8im
 7+0im  8+8im  9+0im

julia> hermitianpart(A)
3×3 Hermitiano{ComplexF64, Matrix{ComplexF64}}:
 1.0+0.0im  3.0+1.0im  5.0-1.5im
 3.0-1.0im  5.0+0.0im  7.0-7.0im
 5.0+1.5im  7.0+7.0im  9.0+0.0im
```

Ten en cuenta que `Hupper` no será igual a `Hlower` a menos que `A` sea en sí misma hermitiana (por ejemplo, si `A == adjoint(A)`).

Todas las partes no reales de la diagonal serán ignoradas.

```julia
Hermitiano(fill(complex(1,1), 1, 1)) == fill(1, 1, 1)
```
