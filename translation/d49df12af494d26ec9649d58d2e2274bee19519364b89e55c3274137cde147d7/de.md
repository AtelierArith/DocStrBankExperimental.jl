```
countfrom(start=1, step=1)
```

Ein Iterator, der unendlich zählt, beginnend bei `start` und um `step` erhöht.

# Beispiele

```jldoctest
julia> for v in Iterators.countfrom(5, 2)
           v > 10 && break
           println(v)
       end
5
7
9
```
