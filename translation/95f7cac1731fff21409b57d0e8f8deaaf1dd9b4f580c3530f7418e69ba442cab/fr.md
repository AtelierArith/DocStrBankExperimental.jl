```
copysign(x, y) -> z
```

Retourne `z` qui a la magnitude de `x` et le même signe que `y`.

# Exemples

```jldoctest
julia> copysign(1, -2)
-1

julia> copysign(-1, 2)
1
```
