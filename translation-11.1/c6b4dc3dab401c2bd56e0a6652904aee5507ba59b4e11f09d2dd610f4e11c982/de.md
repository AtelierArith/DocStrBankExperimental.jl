```
gesdd!(job, A) -> (U, S, VT)
```

Findet die singuläre Wertzerlegung von `A`, `A = U * S * V'`, unter Verwendung eines Divide-and-Conquer-Ansatzes. Wenn `job = A`, werden alle Spalten von `U` und die Zeilen von `V'` berechnet. Wenn `job = N`, werden keine Spalten von `U` oder Zeilen von `V'` berechnet. Wenn `job = O`, wird `A` mit den Spalten von (dünnen) `U` und den Zeilen von (dünnen) `V'` überschrieben. Wenn `job = S`, werden die Spalten von (dünnen) `U` und die Zeilen von (dünnen) `V'` berechnet und separat zurückgegeben.
