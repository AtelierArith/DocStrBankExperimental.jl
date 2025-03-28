```
searchsorted(v, x; by=identity, lt=isless, rev=false)
```

Gibt den Bereich der Indizes in `v` zurück, in dem die Werte gleich `x` sind, oder einen leeren Bereich, der am Einfügepunkt liegt, wenn `v` keine Werte enthält, die gleich `x` sind. Der Vektor `v` muss gemäß der durch die Schlüsselwörter definierten Reihenfolge sortiert sein. Siehe [`sort!`](@ref) für die Bedeutung der Schlüsselwörter und die Definition von Äquivalenz. Beachten Sie, dass die `by`-Funktion sowohl auf den gesuchten Wert `x` als auch auf die Werte in `v` angewendet wird.

Der Bereich wird im Allgemeinen mit einer binären Suche gefunden, es gibt jedoch optimierte Implementierungen für einige Eingaben.

Siehe auch: [`searchsortedfirst`](@ref), [`sort!`](@ref), [`insorted`](@ref), [`findall`](@ref).

# Beispiele

```jldoctest
julia> searchsorted([1, 2, 4, 5, 5, 7], 4) # einzelnes Match
3:3

julia> searchsorted([1, 2, 4, 5, 5, 7], 5) # mehrere Matches
4:5

julia> searchsorted([1, 2, 4, 5, 5, 7], 3) # kein Match, in der Mitte einfügen
3:2

julia> searchsorted([1, 2, 4, 5, 5, 7], 9) # kein Match, am Ende einfügen
7:6

julia> searchsorted([1, 2, 4, 5, 5, 7], 0) # kein Match, am Anfang einfügen
1:0

julia> searchsorted([1=>"one", 2=>"two", 2=>"two", 4=>"four"], 2=>"two", by=first) # vergleiche die Schlüssel der Paare
2:3
```
