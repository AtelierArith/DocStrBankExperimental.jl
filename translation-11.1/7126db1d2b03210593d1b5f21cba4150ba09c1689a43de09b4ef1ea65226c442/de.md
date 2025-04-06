```
trtri!(uplo, diag, A)
```

Findet die Inverse der (oberen, wenn `uplo = U`, unteren, wenn `uplo = L`) Dreiecksmatrix `A`. Wenn `diag = N`, hat `A` nicht-einheitliche Diagonalelemente. Wenn `diag = U`, sind alle Diagonalelemente von `A` eins. `A` wird mit seiner Inversen überschrieben.
