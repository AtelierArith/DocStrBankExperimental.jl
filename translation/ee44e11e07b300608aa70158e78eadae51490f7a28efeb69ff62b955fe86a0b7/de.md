```
precision(num::AbstractFloat; base::Integer=2)
precision(T::Type; base::Integer=2)
```

Erhalten Sie die Genauigkeit einer Fließkommazahl, wie sie durch die effektive Anzahl der Bits im Signifikand definiert ist, oder die Genauigkeit eines Fließkommatyps `T` (seine aktuelle Standardgenauigkeit, wenn `T` ein variabel präziser Typ wie [`BigFloat`](@ref) ist).

Wenn `base` angegeben ist, gibt es die maximale entsprechende Anzahl von Signifikand-Ziffern in dieser Basis zurück.

!!! compat "Julia 1.8"
    Das `base`-Schlüsselwort erfordert mindestens Julia 1.8.

