```
lu!(F::UmfpackLU, A::AbstractSparseMatrixCSC; check=true, reuse_symbolic=true, q=nothing) -> F::UmfpackLU
```

Berechnet die LU-Zerlegung einer spärlichen Matrix `A`, wobei die symbolische Zerlegung einer bereits vorhandenen LU-Zerlegung, die in `F` gespeichert ist, wiederverwendet wird. Sofern `reuse_symbolic` nicht auf false gesetzt ist, muss die spärliche Matrix `A` ein identisches Nicht-Null-Muster wie die Matrix haben, die zur Erstellung der LU-Zerlegung `F` verwendet wurde, andernfalls wird ein Fehler ausgelöst. Wenn die Größe von `A` und `F` unterschiedlich ist, werden alle Vektoren entsprechend angepasst.

Wenn `check = true` ist, wird ein Fehler ausgelöst, wenn die Zerlegung fehlschlägt. Wenn `check = false` ist, liegt die Verantwortung für die Überprüfung der Gültigkeit der Zerlegung (über [`issuccess`](@ref)) beim Benutzer.

Die Permutation `q` kann entweder ein Permutationsvektor oder `nothing` sein. Wenn kein Permutationsvektor bereitgestellt wird oder `q` `nothing` ist, wird das Standardverfahren von UMFPACK verwendet. Wenn die Permutation nicht nullbasiert ist, wird eine nullbasierte Kopie erstellt.

Siehe auch [`lu`](@ref)

!!! note
    `lu!(F::UmfpackLU, A::AbstractSparseMatrixCSC)` verwendet die UMFPACK-Bibliothek, die Teil von SuiteSparse ist. Da diese Bibliothek nur spärliche Matrizen mit [`Float64`](@ref) oder `ComplexF64`-Elementen unterstützt, wird `lu!` die Typen automatisch in die von der LU-Zerlegung festgelegten oder `SparseMatrixCSC{ComplexF64}`-Typen konvertieren, wie es angemessen ist.


!!! compat "Julia 1.5"
    `lu!` für `UmfpackLU` erfordert mindestens Julia 1.5.


# Beispiele

```jldoctest
julia> A = sparse(Float64[1.0 2.0; 0.0 3.0]);

julia> F = lu(A);

julia> B = sparse(Float64[1.0 1.0; 0.0 1.0]);

julia> lu!(F, B);

julia> F \ ones(2)
2-element Vector{Float64}:
 0.0
 1.0
```
