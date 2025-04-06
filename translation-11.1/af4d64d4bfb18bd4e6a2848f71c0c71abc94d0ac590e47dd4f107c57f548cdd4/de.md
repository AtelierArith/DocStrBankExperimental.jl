```
LinearAlgebra.Givens(i1,i2,c,s) -> G
```

Ein Givens-Rotationslinearoperator. Die Felder `c` und `s` repräsentieren den Kosinus und den Sinus des Rotationswinkels. Der `Givens`-Typ unterstützt die linke Multiplikation `G*A` und die konjugiert-transponierte rechte Multiplikation `A*G'`. Der Typ hat keine `size` und kann daher mit Matrizen beliebiger Größe multipliziert werden, solange `i2<=size(A,2)` für `G*A` oder `i2<=size(A,1)` für `A*G'`.

Siehe auch [`givens`](@ref).
