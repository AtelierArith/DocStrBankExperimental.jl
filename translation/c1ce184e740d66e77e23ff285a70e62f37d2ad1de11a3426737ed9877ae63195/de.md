```
stein!(dv, ev_in, w_in, iblock_in, isplit_in)
```

Berechnet die Eigenvektoren für eine symmetrische tridiagonale Matrix mit `dv` als Diagonale und `ev_in` als Nebendiagonale. `w_in` gibt die Eingabeeigenwerte an, für die entsprechende Eigenvektoren gefunden werden sollen. `iblock_in` gibt die Untermatrizen an, die den Eigenwerten in `w_in` entsprechen. `isplit_in` gibt die Trennpunkte zwischen den Untermatrixblöcken an.
