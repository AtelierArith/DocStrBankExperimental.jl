```
middle(a::AbstractArray)
```

Berechne die Mitte eines Arrays `a`, indem die Extrema gefunden und dann deren Mittelwert berechnet werden.

```jldoctest
julia> using Statistics

julia> middle(1:10)
5.5

julia> a = [1,2,3.6,10.9]
4-element Vector{Float64}:
  1.0
  2.0
  3.6
 10.9

julia> middle(a)
5.95
```
