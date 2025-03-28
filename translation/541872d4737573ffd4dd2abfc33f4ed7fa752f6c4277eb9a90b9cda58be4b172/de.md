```
ordschur(F::Schur, select::Union{Vector{Bool},BitVector}) -> F::Schur
```

Ordnet die Schur-Zerlegung `F` einer Matrix `A = Z*T*Z'` gemäß dem logischen Array `select` neu und gibt das neu angeordnete Zerlegungsobjekt `F` zurück. Die ausgewählten Eigenwerte erscheinen in der Hauptdiagonalen von `F.Schur` und die entsprechenden führenden Spalten von `F.vectors` bilden eine orthogonale/einheitliche Basis des entsprechenden rechtsinvarianten Unterraums. Im reellen Fall muss ein komplex konjugiertes Eigenwertpaar entweder vollständig einbezogen oder vollständig ausgeschlossen werden über `select`.
