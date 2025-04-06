```
mul!(Y, A, B) -> Y
```

Berechnet das Matrix-Matrix- oder Matrix-Vektor-Produkt $A B$ und speichert das Ergebnis in `Y`, wobei der vorhandene Wert von `Y` überschrieben wird. Beachten Sie, dass `Y` nicht mit `A` oder `B` aliasiert sein darf.

# Beispiele

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]; B = [1.0 1.0; 1.0 1.0]; Y = similar(B);

julia> mul!(Y, A, B) === Y
true

julia> Y
2×2 Matrix{Float64}:
 3.0  3.0
 7.0  7.0

julia> Y == A * B
true
```

# Implementierung

Für benutzerdefinierte Matrix- und Vektortypen wird empfohlen, die 5-Argumente `mul!` zu implementieren, anstatt direkt die 3-Argumente `mul!` zu implementieren, wenn möglich.
