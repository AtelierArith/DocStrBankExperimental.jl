```
trsen!(job, compq, select, T, Q) -> (T, Q, w, s, sep)
trsen!(select, T, Q) -> (T, Q, w, s, sep)
```

Ordnet die Schur-Faktorisierung einer Matrix neu und findet optional reziproke Konditionszahlen. Wenn `job = N`, werden keine Konditionszahlen gefunden. Wenn `job = E`, wird nur die Konditionszahl für diesen Cluster von Eigenwerten gefunden. Wenn `job = V`, wird nur die Konditionszahl für den invarianten Unterraum gefunden. Wenn `job = B`, werden die Konditionszahlen für den Cluster und den Unterraum gefunden. Wenn `compq = V`, werden die Schur-Vektoren `Q` aktualisiert. Wenn `compq = N`, werden die Schur-Vektoren nicht modifiziert. `select` bestimmt, welche Eigenwerte im Cluster sind. Die 3-Argument-Methode ruft die 5-Argument-Methode mit `job = N` und `compq = V` auf.

Gibt `T`, `Q`, neu angeordnete Eigenwerte in `w`, die Konditionszahl des Clusters von Eigenwerten `s` und die Konditionszahl des invarianten Unterraums `sep` zurück.
