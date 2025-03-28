```
gecon!(normtype, A, anorm)
```

Findet die reziproke Konditionszahl der Matrix `A`. Wenn `normtype = I`, wird die Konditionszahl in der Unendlichkeit-Norm gefunden. Wenn `normtype = O` oder `1`, wird die Konditionszahl in der Eins-Norm gefunden. `A` muss das Ergebnis von `getrf!` sein und `anorm` ist die Norm von `A` in der relevanten Norm.
