```
ldiv!(A::Tridiagonal, B::AbstractVecOrMat) -> B
```

Berechne `A \ B` in-place durch Gaußsche Eliminierung mit partieller Pivotierung und speichere das Ergebnis in `B`, wobei das Ergebnis zurückgegeben wird. Dabei werden auch die Diagonalen von `A` überschrieben.

!!! compat "Julia 1.11"
    `ldiv!` für `Tridiagonal` linke Seiten erfordert mindestens Julia 1.11.

