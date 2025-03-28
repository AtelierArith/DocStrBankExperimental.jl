```
middle(a::AbstractArray)
```

Calcula el punto medio de un arreglo `a`, que consiste en encontrar sus extremos y luego calcular su media.

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
