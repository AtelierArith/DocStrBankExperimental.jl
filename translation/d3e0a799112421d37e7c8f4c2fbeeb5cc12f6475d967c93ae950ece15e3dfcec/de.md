```
diff(A::AbstractVector)
diff(A::AbstractArray; dims::Integer)
```

Endlicher Differenzenoperator auf einem Vektor oder einem mehrdimensionalen Array `A`. Im letzteren Fall muss die Dimension, auf der gearbeitet werden soll, mit dem Schlüsselwortargument `dims` angegeben werden.

!!! compat "Julia 1.1"
    `diff` für Arrays mit einer Dimension höher als 2 erfordert mindestens Julia 1.1.


# Beispiele

```jldoctest
julia> a = [2 4; 6 16]
2×2 Matrix{Int64}:
 2   4
 6  16

julia> diff(a, dims=2)
2×1 Matrix{Int64}:
  2
 10

julia> diff(vec(a))
3-element Vector{Int64}:
  4
 -2
 12
```
