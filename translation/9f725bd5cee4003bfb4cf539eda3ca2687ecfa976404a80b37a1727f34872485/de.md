```
typeintersect(T::Type, S::Type)
```

Berechne einen Typ, der die Schnittmenge von `T` und `S` enthält. Normalerweise wird dies der kleinste solche Typ oder einer, der ihm nahe kommt, sein.

Ein Sonderfall, in dem das genaue Verhalten garantiert ist: wenn `T <: S`, dann gilt `typeintersect(S, T) == T == typeintersect(T, S)`.
