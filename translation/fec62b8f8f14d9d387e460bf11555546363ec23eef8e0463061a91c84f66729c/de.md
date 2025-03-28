```
wo
```

Das `where`-Schlüsselwort erstellt einen [`UnionAll`](@ref)-Typ, der als eine iterierte Vereinigung anderer Typen über alle Werte einer Variablen betrachtet werden kann. Zum Beispiel umfasst `Vector{T} where T<:Real` alle [`Vector`](@ref)s, bei denen der Elementtyp eine Art von `Real`-Zahl ist.

Die Variablenbindung hat standardmäßig [`Any`](@ref), wenn sie weggelassen wird:

```julia
Vector{T} where T    # kurz für `where T<:Any`
```

Variablen können auch untere Schranken haben:

```julia
Vector{T} where T>:Int
Vector{T} where Int<:T<:Real
```

Es gibt auch eine prägnante Syntax für geschachtelte `where`-Ausdrücke. Zum Beispiel kann dies:

```julia
Pair{T, S} where S<:Array{T} where T<:Number
```

verkürzt werden zu:

```julia
Pair{T, S} where {T<:Number, S<:Array{T}}
```

Diese Form findet sich häufig in Methodensignaturen.

Beachten Sie, dass in dieser Form die Variablen äußerste zuerst aufgelistet sind. Dies entspricht der Reihenfolge, in der Variablen substituiert werden, wenn ein Typ mit den Parameterwerten unter Verwendung der Syntax `T{p1, p2, ...}` "angewendet" wird.
