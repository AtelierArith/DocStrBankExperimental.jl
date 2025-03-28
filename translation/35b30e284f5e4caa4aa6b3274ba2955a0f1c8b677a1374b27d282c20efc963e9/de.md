```
prepend!(a::Vector, collections...) -> collection
```

Fügen Sie die Elemente jeder `collections` am Anfang von `a` ein.

Wenn `collections` mehrere Sammlungen angibt, bleibt die Reihenfolge erhalten: Die Elemente von `collections[1]` erscheinen am weitesten links in `a`, und so weiter.

!!! compat "Julia 1.6"
    Das Angeben mehrerer Sammlungen, die hinzugefügt werden sollen, erfordert mindestens Julia 1.6.


# Beispiele

```jldoctest
julia> prepend!([3], [1, 2])
3-element Vector{Int64}:
 1
 2
 3

julia> prepend!([6], [1, 2], [3, 4, 5])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```
