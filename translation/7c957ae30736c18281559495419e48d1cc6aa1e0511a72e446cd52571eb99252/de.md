```
stev!(job, dv, ev) -> (dv, Zmat)
```

Berechnet das Eigenwertsystem für eine symmetrische tridiagonale Matrix mit `dv` als Diagonale und `ev` als Nebendiagonale. Wenn `job = N`, werden nur die Eigenwerte gefunden und in `dv` zurückgegeben. Wenn `job = V`, werden auch die Eigenvektoren gefunden und in `Zmat` zurückgegeben.
