```
isreal(x) -> Bool
```

Testen Sie, ob `x` oder alle seine Elemente numerisch gleich einer reellen Zahl sind, einschließlich Unendlichkeiten und NaNs. `isreal(x)` ist wahr, wenn `isequal(x, real(x))` wahr ist.

# Beispiele

```jldoctest
julia> isreal(5.)
true

julia> isreal(1 - 3im)
false

julia> isreal(Inf + 0im)
true

julia> isreal([4.; complex(0,1)])
false
```
