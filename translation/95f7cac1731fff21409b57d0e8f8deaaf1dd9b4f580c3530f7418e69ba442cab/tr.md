```
copysign(x, y) -> z
```

`z`'yi `x`'in büyüklüğüne ve `y`'nin aynı işaretine sahip olacak şekilde döndürün.

# Örnekler

```jldoctest
julia> copysign(1, -2)
-1

julia> copysign(-1, 2)
1
```
