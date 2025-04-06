```
middle(a::AbstractArray)
```

Calcule le milieu d'un tableau `a`, ce qui consiste à trouver ses extrêmes puis à calculer leur moyenne.

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
