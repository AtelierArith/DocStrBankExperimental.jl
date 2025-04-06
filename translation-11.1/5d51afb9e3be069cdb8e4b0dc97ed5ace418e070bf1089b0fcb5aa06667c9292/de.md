```
ordschur(F::GeneralizedSchur, select::Union{Vector{Bool},BitVector}) -> F::GeneralizedSchur
```

Ordnet die verallgemeinerte Schur-Faktorisierung `F` eines Matrixpaars `(A, B) = (Q*S*Z', Q*T*Z')` gemäß dem logischen Array `select` neu und gibt ein GeneralizedSchur-Objekt `F` zurück. Die ausgewählten Eigenwerte erscheinen in der Hauptdiagonalen von sowohl `F.S` als auch `F.T`, und die linken und rechten orthogonalen/einheitlichen Schur-Vektoren werden ebenfalls so umgeordnet, dass `(A, B) = F.Q*(F.S, F.T)*F.Z'` weiterhin gilt und die verallgemeinerten Eigenwerte von `A` und `B` weiterhin mit `F.α./F.β` erhalten werden können.
