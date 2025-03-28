```
searchsortedfirst(v, x; by=identity, lt=isless, rev=false)
```

Gibt den Index des ersten Wertes in `v` zurück, der nicht vor `x` geordnet ist. Wenn alle Werte in `v` vor `x` geordnet sind, wird `lastindex(v) + 1` zurückgegeben.

Der Vektor `v` muss gemäß der durch die Schlüsselwörter definierten Reihenfolge sortiert sein. Das Einfügen von `x` an dem zurückgegebenen Index wird die sortierte Reihenfolge beibehalten. Siehe [`sort!`](@ref) für die Bedeutung und Verwendung der Schlüsselwörter. Beachten Sie, dass die `by`-Funktion sowohl auf den gesuchten Wert `x` als auch auf die Werte in `v` angewendet wird.

Der Index wird normalerweise mit einer binären Suche gefunden, es gibt jedoch optimierte Implementierungen für einige Eingaben.

Siehe auch: [`searchsortedlast`](@ref), [`searchsorted`](@ref), [`findfirst`](@ref).

# Beispiele

```jldoctest
julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 4) # einzelnes Match
3

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 5) # mehrere Matches
4

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 3) # kein Match, in der Mitte einfügen
3

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 9) # kein Match, am Ende einfügen
7

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 0) # kein Match, am Anfang einfügen
1

julia> searchsortedfirst([1=>"one", 2=>"two", 4=>"four"], 3=>"three", by=first) # vergleiche die Schlüssel der Paare
3
```
