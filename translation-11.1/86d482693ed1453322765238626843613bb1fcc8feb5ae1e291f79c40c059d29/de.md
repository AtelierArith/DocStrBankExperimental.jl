```
Hermitian(A::AbstractMatrix, uplo::Symbol=:U)
```

Konstruiere eine `Hermitian`-Ansicht des oberen (wenn `uplo = :U`) oder unteren (wenn `uplo = :L`) Dreiecks der Matrix `A`.

Um den hermiteschen Teil von `A` zu berechnen, verwende [`hermitianpart`](@ref).

# Beispiele

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

Beachte, dass `Hupper` nicht gleich `Hlower` sein wird, es sei denn, `A` ist selbst hermitesch (z. B. wenn `A == adjoint(A)`).

Alle nicht-reellen Teile der Diagonalen werden ignoriert.

```julia
Hermitian(fill(complex(1,1), 1, 1)) == fill(1, 1, 1)
```
