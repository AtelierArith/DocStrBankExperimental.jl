```
searchsortedlast(v, x; by=identity, lt=isless, rev=false)
```

Gibt den Index des letzten Wertes in `v` zurück, der nicht nach `x` geordnet ist. Wenn alle Werte in `v` nach `x` geordnet sind, wird `firstindex(v) - 1` zurückgegeben.

Der Vektor `v` muss gemäß der durch die Schlüsselwörter definierten Reihenfolge sortiert sein. Das `insert!` von `x` unmittelbar nach dem zurückgegebenen Index wird die sortierte Reihenfolge beibehalten. Siehe [`sort!`](@ref) für die Bedeutung und Verwendung der Schlüsselwörter. Beachten Sie, dass die `by`-Funktion sowohl auf den gesuchten Wert `x` als auch auf die Werte in `v` angewendet wird.

Der Index wird im Allgemeinen mit einer binären Suche gefunden, es gibt jedoch optimierte Implementierungen für einige Eingaben.

# Beispiele

```jldoctest
julia> searchsortedlast([1, 2, 4, 5, 5, 7], 4) # einzelnes Match
3

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 5) # mehrere Matches
5

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 3) # kein Match, in der Mitte einfügen
2

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 9) # kein Match, am Ende einfügen
6

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 0) # kein Match, am Anfang einfügen
0

julia> searchsortedlast([1=>"one", 2=>"two", 4=>"four"], 3=>"three", by=first) # vergleiche die Schlüssel der Paare
2
```
