```
trevc!(seite, wieviele, auswählen, T, VL = similar(T), VR = similar(T))
```

Findet das Eigenwertsystem einer oberen Dreiecksmatrix `T`. Wenn `seite = R`, werden die rechten Eigenvektoren berechnet. Wenn `seite = L`, werden die linken Eigenvektoren berechnet. Wenn `seite = B`, werden beide Mengen berechnet. Wenn `wieviele = A`, werden alle Eigenvektoren gefunden. Wenn `wieviele = B`, werden alle Eigenvektoren gefunden und mit `VL` und `VR` zurücktransformiert. Wenn `wieviele = S`, werden nur die Eigenvektoren berechnet, die den Werten in `auswählen` entsprechen.
