```
GeneralizedSchur <: Faktorisierung
```

Matrixfaktorisierungstyp der verallgemeinerten Schur-Faktorisierung von zwei Matrizen `A` und `B`. Dies ist der Rückgabetyp von [`schur(_, _)`](@ref), der entsprechenden Matrixfaktorisierungsfunktion.

Wenn `F::GeneralizedSchur` das Faktorisierungsobjekt ist, können die (quasi) dreieckigen Schur-Faktoren über `F.S` und `F.T` erhalten werden, die linken unitären/orthogonalen Schur-Vektoren über `F.left` oder `F.Q`, und die rechten unitären/orthogonalen Schur-Vektoren können mit `F.right` oder `F.Z` erhalten werden, sodass `A=F.left*F.S*F.right'` und `B=F.left*F.T*F.right'`. Die verallgemeinerten Eigenwerte von `A` und `B` können mit `F.α./F.β` erhalten werden.

Das Iterieren der Zerlegung produziert die Komponenten `F.S`, `F.T`, `F.Q`, `F.Z`, `F.α` und `F.β`.
