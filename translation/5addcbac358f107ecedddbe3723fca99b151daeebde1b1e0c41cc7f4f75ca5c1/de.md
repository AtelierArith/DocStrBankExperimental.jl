```
spr!(uplo, α, x, AP)
```

Aktualisiere die Matrix `A` als `A+α*x*x'`, wobei `A` eine symmetrische Matrix ist, die im gepackten Format `AP` bereitgestellt wird und `x` ein Vektor ist.

Mit `uplo = 'U'` muss das Array AP den oberen Dreiecksteil der symmetrischen Matrix sequenziell, spaltenweise enthalten, sodass `AP[1]` `A[1, 1]` enthält, `AP[2]` und `AP[3]` `A[1, 2]` und `A[2, 2]` enthalten, und so weiter.

Mit `uplo = 'L'` muss das Array AP den unteren Dreiecksteil der symmetrischen Matrix sequenziell, spaltenweise enthalten, sodass `AP[1]` `A[1, 1]` enthält, `AP[2]` und `AP[3]` `A[2, 1]` und `A[3, 1]` enthalten, und so weiter.

Der skalare Eingabewert `α` muss reell sein.

Die Array-Eingaben `x` und `AP` müssen alle vom Typ `Float32` oder `Float64` sein. Gib das aktualisierte `AP` zurück.

!!! compat "Julia 1.8"
    `spr!` erfordert mindestens Julia 1.8.

