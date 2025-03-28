```
insorted(x, v; by=identity, lt=isless, rev=false) -> Bool
```

Bestimmen Sie, ob ein Vektor `v` einen Wert enthält, der `x` entspricht. Der Vektor `v` muss gemäß der durch die Schlüsselwörter definierten Reihenfolge sortiert sein. Siehe [`sort!`](@ref) für die Bedeutung der Schlüsselwörter und die Definition von Äquivalenz. Beachten Sie, dass die `by`-Funktion sowohl auf den gesuchten Wert `x` als auch auf die Werte in `v` angewendet wird.

Die Überprüfung erfolgt in der Regel mithilfe einer binären Suche, es gibt jedoch optimierte Implementierungen für einige Eingaben.

Siehe auch [`in`](@ref).

# Beispiele

```jldoctest
julia> insorted(4, [1, 2, 4, 5, 5, 7]) # einzelnes Vorkommen
true

julia> insorted(5, [1, 2, 4, 5, 5, 7]) # mehrere Vorkommen
true

julia> insorted(3, [1, 2, 4, 5, 5, 7]) # kein Vorkommen
false

julia> insorted(9, [1, 2, 4, 5, 5, 7]) # kein Vorkommen
false

julia> insorted(0, [1, 2, 4, 5, 5, 7]) # kein Vorkommen
false

julia> insorted(2=>"ZWEI", [1=>"eins", 2=>"zwei", 4=>"vier"], by=first) # vergleichen Sie die Schlüssel der Paare
true
```

!!! compat "Julia 1.6"
    `insorted` wurde in Julia 1.6 hinzugefügt.

