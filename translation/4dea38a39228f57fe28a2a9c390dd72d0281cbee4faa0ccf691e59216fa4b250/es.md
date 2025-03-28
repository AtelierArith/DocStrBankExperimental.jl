```
BitArray(itr)
```

Construye un [`BitArray`](@ref) generado por el objeto iterable dado. La forma se infiere del objeto `itr`.

# Ejemplos

```jldoctest
julia> BitArray([1 0; 0 1])
2×2 BitMatrix:
 1  0
 0  1

julia> BitArray(x+y == 3 for x = 1:2, y = 1:3)
2×3 BitMatrix:
 0  1  0
 1  0  0

julia> BitArray(x+y == 3 for x = 1:2 for y = 1:3)
6-element BitVector:
 0
 1
 0
 1
 0
 0
```
