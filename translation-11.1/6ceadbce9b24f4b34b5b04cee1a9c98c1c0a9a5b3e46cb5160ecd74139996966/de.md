```
gesvd!(jobu, jobvt, A) -> (U, S, VT)
```

Findet die singuläre Wertzerlegung von `A`, `A = U * S * V'`. Wenn `jobu = A`, werden alle Spalten von `U` berechnet. Wenn `jobvt = A`, werden alle Zeilen von `V'` berechnet. Wenn `jobu = N`, werden keine Spalten von `U` berechnet. Wenn `jobvt = N`, werden keine Zeilen von `V'` berechnet. Wenn `jobu = O`, wird `A` mit den Spalten von (dünnen) `U` überschrieben. Wenn `jobvt = O`, wird `A` mit den Zeilen von (dünnen) `V'` überschrieben. Wenn `jobu = S`, werden die Spalten von (dünnen) `U` berechnet und separat zurückgegeben. Wenn `jobvt = S`, werden die Zeilen von (dünnen) `V'` berechnet und separat zurückgegeben. `jobu` und `jobvt` können nicht beide `O` sein.

Gibt `U`, `S` und `Vt` zurück, wobei `S` die singulären Werte von `A` sind.
