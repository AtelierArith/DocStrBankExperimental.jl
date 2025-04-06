```
maxintfloat(T=Float64)
```

Die größte aufeinanderfolgende ganzzahlige Fließkommazahl, die genau im gegebenen Fließkommatyp `T` (der standardmäßig auf `Float64` gesetzt ist) dargestellt wird.

Das heißt, `maxintfloat` gibt die kleinste positive ganzzahlige Fließkommazahl `n` zurück, so dass `n+1` *nicht* genau im Typ `T` darstellbar ist.

Wenn ein Wert vom Typ `Integer` benötigt wird, verwenden Sie `Integer(maxintfloat(T))`.
