```
middle(a::AbstractArray)
```

Bir dizi `a`nın ortasını hesaplayın, bu, onun ekstremalarını bulmayı ve ardından bunların ortalamasını hesaplamayı içerir.

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
