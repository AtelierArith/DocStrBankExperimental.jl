```
rdiv!(A, B)
```

Berechnet `A / B` im Platz und überschreibt `A`, um das Ergebnis zu speichern.

Das Argument `B` sollte *kein* Matrix sein. Stattdessen sollte es ein Faktorisierungsobjekt sein (z. B. erzeugt durch [`factorize`](@ref) oder [`cholesky`](@ref)). Der Grund dafür ist, dass die Faktorisierung selbst sowohl teuer ist als auch typischerweise Speicher allokiert (obwohl sie auch im Platz durchgeführt werden kann, z. B. durch [`lu!`](@ref)), und leistungs-kritische Situationen, die `rdiv!` erfordern, normalerweise auch eine feinkörnige Kontrolle über die Faktorisierung von `B` erfordern.

!!! note
    Bestimmte strukturierte Matrizenarten, wie `Diagonal` und `UpperTriangular`, sind erlaubt, da diese bereits in einer faktorisierte Form vorliegen.

