```
chop(s::AbstractString; head::Integer = 0, tail::Integer = 1)
```

Entfernt die ersten `head` und die letzten `tail` Zeichen von `s`. Der Aufruf `chop(s)` entfernt das letzte Zeichen von `s`. Wenn mehr Zeichen entfernt werden sollen als `length(s)`, wird ein leerer String zurückgegeben.

Siehe auch [`chomp`](@ref), [`startswith`](@ref), [`first`](@ref).

# Beispiele

```jldoctest
julia> a = "März"
"März"

julia> chop(a)
"Mar"

julia> chop(a, head = 1, tail = 2)
"är"

julia> chop(a, head = 5, tail = 5)
""
```
