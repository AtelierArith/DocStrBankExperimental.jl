```
flipsign(x, y)
```

`y` negatifse `x`'in işaretini tersine çevirir. Örneğin `abs(x) = flipsign(x,x)`.

# Örnekler

```jldoctest
julia> flipsign(5, 3)
5

julia> flipsign(5, -3)
-5
```
