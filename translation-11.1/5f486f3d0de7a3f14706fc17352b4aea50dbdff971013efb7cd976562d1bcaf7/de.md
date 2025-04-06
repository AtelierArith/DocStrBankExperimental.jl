```
geqrf!(A, tau)
```

Berechnet die `QR`-Faktorisierung von `A`, `A = QR`. `tau` enthält Skalare, die die elementaren Reflektoren der Faktorisierung parametrisieren. `tau` muss eine Länge haben, die größer oder gleich der kleinsten Dimension von `A` ist.

Gibt `A` und `tau` modifiziert in-place zurück.
