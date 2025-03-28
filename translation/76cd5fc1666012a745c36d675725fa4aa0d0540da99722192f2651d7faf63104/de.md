```
trcon!(norm, uplo, diag, A)
```

Findet die reziproke Konditionszahl der (oberen, wenn `uplo = U`, unteren, wenn `uplo = L`) dreieckigen Matrix `A`. Wenn `diag = N`, hat `A` nicht-einheitliche Diagonalelemente. Wenn `diag = U`, sind alle Diagonalelemente von `A` eins. Wenn `norm = I`, wird die Konditionszahl in der Unendlichkeit-Norm gefunden. Wenn `norm = O` oder `1`, wird die Konditionszahl in der Eins-Norm gefunden.
