```
gelqf!(A, tau)
```

Berechnet die `LQ`-Faktorisierung von `A`, `A = LQ`. `tau` enthält Skalare, die die elementaren Reflektoren der Faktorisierung parametrisieren. `tau` muss eine Länge haben, die größer oder gleich der kleinsten Dimension von `A` ist.

Gibt `A` und `tau` modifiziert in-place zurück.
