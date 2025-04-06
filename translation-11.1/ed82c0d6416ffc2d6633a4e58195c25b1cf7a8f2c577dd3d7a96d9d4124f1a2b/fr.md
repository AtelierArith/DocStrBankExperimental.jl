```
flipsign(x, y)
```

Retourne `x` avec son signe inversé si `y` est négatif. Par exemple `abs(x) = flipsign(x,x)`.

# Exemples

```jldoctest
julia> flipsign(5, 3)
5

julia> flipsign(5, -3)
-5
```
