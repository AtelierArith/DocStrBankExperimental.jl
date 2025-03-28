```
continue
```

Überspringen Sie den Rest der aktuellen Schleifeniteration.

# Beispiele

```jldoctest
julia> for i = 1:6
           iseven(i) && continue
           println(i)
       end
1
3
5
```
