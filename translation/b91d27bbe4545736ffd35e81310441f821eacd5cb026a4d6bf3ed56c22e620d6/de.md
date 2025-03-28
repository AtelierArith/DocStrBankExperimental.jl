```
first(s::AbstractString, n::Integer)
```

Holen Sie sich eine Zeichenkette, die aus den ersten `n` Zeichen von `s` besteht.

# Beispiele

```jldoctest
julia> first("∀ϵ≠0: ϵ²>0", 0)
""

julia> first("∀ϵ≠0: ϵ²>0", 1)
"∀"

julia> first("∀ϵ≠0: ϵ²>0", 3)
"∀ϵ≠"
```
