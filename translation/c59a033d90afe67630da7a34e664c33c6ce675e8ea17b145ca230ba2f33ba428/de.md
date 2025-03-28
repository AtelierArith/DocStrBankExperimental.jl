```
schur(A, B) -> F::GeneralizedSchur
```

Berechnet die verallgemeinerte Schur- (oder QZ-) Faktorisierung der Matrizen `A` und `B`. Die (quasi) dreieckigen Schur-Faktoren können aus dem `Schur`-Objekt `F` mit `F.S` und `F.T` erhalten werden, die linken unitären/orthogonalen Schur-Vektoren können mit `F.left` oder `F.Q` und die rechten unitären/orthogonalen Schur-Vektoren können mit `F.right` oder `F.Z` erhalten werden, sodass `A=F.left*F.S*F.right'` und `B=F.left*F.T*F.right'`. Die verallgemeinerten Eigenwerte von `A` und `B` können mit `F.α./F.β` erhalten werden.

Das Iterieren der Zerlegung produziert die Komponenten `F.S`, `F.T`, `F.Q`, `F.Z`, `F.α` und `F.β`.
