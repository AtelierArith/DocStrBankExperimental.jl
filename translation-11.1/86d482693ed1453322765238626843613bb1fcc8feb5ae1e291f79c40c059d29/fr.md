```
Hermitian(A::AbstractMatrix, uplo::Symbol=:U)
```

Construit une vue `Hermitian` du triangle supérieur (si `uplo = :U`) ou inférieur (si `uplo = :L`) de la matrice `A`.

Pour calculer la partie hermitienne de `A`, utilisez [`hermitianpart`](@ref).

# Exemples

```jldoctest
julia> A = [1 2+2im 3-3im; 4 5 6-6im; 7 8+8im 9]
3×3 Matrix{Complex{Int64}}:
 1+0im  2+2im  3-3im
 4+0im  5+0im  6-6im
 7+0im  8+8im  9+0im

julia> Hupper = Hermitian(A)
3×3 Hermitian{Complex{Int64}, Matrix{Complex{Int64}}}:
 1+0im  2+2im  3-3im
 2-2im  5+0im  6-6im
 3+3im  6+6im  9+0im

julia> Hlower = Hermitian(A, :L)
3×3 Hermitian{Complex{Int64}, Matrix{Complex{Int64}}}:
 1+0im  4+0im  7+0im
 4+0im  5+0im  8-8im
 7+0im  8+8im  9+0im

julia> hermitianpart(A)
3×3 Hermitian{ComplexF64, Matrix{ComplexF64}}:
 1.0+0.0im  3.0+1.0im  5.0-1.5im
 3.0-1.0im  5.0+0.0im  7.0-7.0im
 5.0+1.5im  7.0+7.0im  9.0+0.0im
```

Notez que `Hupper` ne sera pas égal à `Hlower` à moins que `A` ne soit lui-même hermitien (par exemple, si `A == adjoint(A)`).

Toutes les parties non réelles de la diagonale seront ignorées.

```julia
Hermitian(fill(complex(1,1), 1, 1)) == fill(1, 1, 1)
```
