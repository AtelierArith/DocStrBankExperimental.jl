```
Symmetrisch(A::AbstractMatrix, uplo::Symbol=:U)
```

Konstruiert eine `Symmetrisch`-Ansicht des oberen (wenn `uplo = :U`) oder unteren (wenn `uplo = :L`) Dreiecks der Matrix `A`.

`Symmetrisch`-Ansichten sind hauptsächlich nützlich für reelle symmetrische Matrizen, für die spezialisierte Algorithmen (z. B. für Eigenwertprobleme) für `Symmetrisch`-Typen aktiviert sind. Allgemeiner siehe auch [`Hermitian(A)`](@ref) für hermitische Matrizen `A == A'`, die effektiv äquivalent zu `Symmetrisch` für reelle Matrizen sind, aber auch für komplexe Matrizen nützlich sind. (Während komplexe `Symmetrisch`-Matrizen unterstützt werden, gibt es nur wenige, wenn überhaupt, spezialisierte Algorithmen.)

Um den symmetrischen Teil einer reellen Matrix oder allgemeiner den hermitischen Teil `(A + A') / 2` einer reellen oder komplexen Matrix `A` zu berechnen, verwenden Sie [`hermitianpart`](@ref).

# Beispiele

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> Supper = Symmetrisch(A)
3×3 Symmetrisch{Int64, Matrix{Int64}}:
 1  2  3
 2  5  6
 3  6  9

julia> Slower = Symmetrisch(A, :L)
3×3 Symmetrisch{Int64, Matrix{Int64}}:
 1  4  7
 4  5  8
 7  8  9

julia> hermitianpart(A)
3×3 Hermitian{Float64, Matrix{Float64}}:
 1.0  3.0  5.0
 3.0  5.0  7.0
 5.0  7.0  9.0
```

Beachten Sie, dass `Supper` nicht gleich `Slower` sein wird, es sei denn, `A` ist selbst symmetrisch (z. B. wenn `A == transpose(A)`).
