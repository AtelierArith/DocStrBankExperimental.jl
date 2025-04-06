```
last(s::AbstractString, n::Integer)
```

Holen Sie sich eine Zeichenkette, die aus den letzten `n` Zeichen von `s` besteht.

# Beispiele

```jldoctest
julia> last("∀ϵ≠0: ϵ²>0", 0)
""

julia> last("∀ϵ≠0: ϵ²>0", 1)
"0"

julia> last("∀ϵ≠0: ϵ²>0", 3)
"²>0"
```
