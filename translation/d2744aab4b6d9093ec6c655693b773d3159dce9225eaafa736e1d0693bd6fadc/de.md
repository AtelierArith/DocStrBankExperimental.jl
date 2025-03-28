```
keepat!(a::Vector, inds)
keepat!(a::BitVector, inds)
```

Entferne die Elemente an allen Indizes, die nicht durch `inds` angegeben sind, und gebe das modifizierte `a` zurück. Die behaltenen Elemente werden verschoben, um die resultierenden Lücken zu füllen.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein veränderter Parameter Speicher mit einem anderen Parameter teilt.


`inds` muss ein Iterator von sortierten und einzigartigen ganzzahligen Indizes sein. Siehe auch [`deleteat!`](@ref).

!!! compat "Julia 1.7"
    Diese Funktion ist seit Julia 1.7 verfügbar.


# Beispiele

```jldoctest
julia> keepat!([6, 5, 4, 3, 2, 1], 1:2:5)
3-element Vector{Int64}:
 6
 4
 2
```
