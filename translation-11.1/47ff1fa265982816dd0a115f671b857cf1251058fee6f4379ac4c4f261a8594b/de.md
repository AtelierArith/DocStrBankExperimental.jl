```
digits!(array, n::Integer; base::Integer = 10)
```

Füllt ein Array mit den Ziffern von `n` in der angegebenen Basis. Die bedeutenderen Ziffern befinden sich an höheren Indizes. Wenn die Array-Länge nicht ausreicht, werden die am wenigsten signifikanten Ziffern bis zur Array-Länge gefüllt. Wenn die Array-Länge übermäßig ist, wird der überschüssige Teil mit Nullen gefüllt.

# Beispiele

```jldoctest
julia> digits!([2, 2, 2, 2], 10, base = 2)
4-element Vector{Int64}:
 0
 1
 0
 1

julia> digits!([2, 2, 2, 2, 2, 2], 10, base = 2)
6-element Vector{Int64}:
 0
 1
 0
 1
 0
 0
```
