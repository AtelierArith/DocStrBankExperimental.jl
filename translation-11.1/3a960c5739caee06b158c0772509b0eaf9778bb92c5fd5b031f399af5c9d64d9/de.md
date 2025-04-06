```
UpperHessenberg(A::AbstractMatrix)
```

Konstruiere eine `UpperHessenberg`-Ansicht der Matrix `A`. Einträge von `A` unterhalb der ersten Subdiagonale werden ignoriert.

!!! compat "Julia 1.3"
    Dieser Typ wurde in Julia 1.3 hinzugefügt.


Effiziente Algorithmen sind für `H \ b`, `det(H)` und Ähnliches implementiert.

Siehe auch die [`hessenberg`](@ref) Funktion, um jede Matrix in eine ähnliche obere Hessenberg-Matrix zu faktorisieren.

Wenn `F::Hessenberg` das Faktorisierungsobjekt ist, kann die unitäre Matrix mit `F.Q` und die Hessenberg-Matrix mit `F.H` abgerufen werden. Wenn `Q` extrahiert wird, ist der resultierende Typ das `HessenbergQ`-Objekt und kann mit [`convert(Array, _)`](@ref) (oder `Array(_)` kurz) in eine reguläre Matrix umgewandelt werden.

Das Iterieren über die Zerlegung erzeugt die Faktoren `F.Q` und `F.H`.

# Beispiele

```jldoctest
julia> A = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
4×4 Matrix{Int64}:
  1   2   3   4
  5   6   7   8
  9  10  11  12
 13  14  15  16

julia> UpperHessenberg(A)
4×4 UpperHessenberg{Int64, Matrix{Int64}}:
 1   2   3   4
 5   6   7   8
 ⋅  10  11  12
 ⋅   ⋅  15  16
```
