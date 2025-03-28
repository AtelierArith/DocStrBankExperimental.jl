```
filter!(f, a)
```

Aktualisiert die Sammlung `a`, indem Elemente entfernt werden, für die `f` `false` ist. Die Funktion `f` erhält ein Argument.

# Beispiele

```jldoctest
julia> filter!(isodd, Vector(1:10))
5-element Vector{Int64}:
 1
 3
 5
 7
 9
```
