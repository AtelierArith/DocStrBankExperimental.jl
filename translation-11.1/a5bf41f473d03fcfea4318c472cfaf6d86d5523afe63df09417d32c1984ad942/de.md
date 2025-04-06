```
partialsort!(v, k; by=identity, lt=isless, rev=false)
```

Sortiere den Vektor `v` teilweise in-place, sodass der Wert am Index `k` (oder der Bereich benachbarter Werte, wenn `k` ein Bereich ist) an der Position erscheint, an der er erscheinen würde, wenn das Array vollständig sortiert wäre. Wenn `k` ein einzelner Index ist, wird dieser Wert zurückgegeben; wenn `k` ein Bereich ist, wird ein Array von Werten an diesen Indizes zurückgegeben. Beachte, dass `partialsort!` das Eingangsarray möglicherweise nicht vollständig sortiert.

Für die Schlüsselwortargumente siehe die Dokumentation von [`sort!`](@ref).

# Beispiele

```jldoctest
julia> a = [1, 2, 4, 3, 4]
5-element Vector{Int64}:
 1
 2
 4
 3
 4

julia> partialsort!(a, 4)
4

julia> a
5-element Vector{Int64}:
 1
 2
 3
 4
 4

julia> a = [1, 2, 4, 3, 4]
5-element Vector{Int64}:
 1
 2
 4
 3
 4

julia> partialsort!(a, 4, rev=true)
2

julia> a
5-element Vector{Int64}:
 4
 4
 3
 2
 1
```
