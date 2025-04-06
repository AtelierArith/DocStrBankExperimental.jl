```
count([f=identity,] A::AbstractArray; dims=:)
```

Zähle die Anzahl der Elemente in `A`, für die `f` `true` zurückgibt, über die angegebenen Dimensionen.

!!! compat "Julia 1.5"
    Das `dims`-Schlüsselwort wurde in Julia 1.5 hinzugefügt.


!!! compat "Julia 1.6"
    Das `init`-Schlüsselwort wurde in Julia 1.6 hinzugefügt.


# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> count(<=(2), A, dims=1)
1×2 Matrix{Int64}:
 1  1

julia> count(<=(2), A, dims=2)
2×1 Matrix{Int64}:
 2
 0
```
