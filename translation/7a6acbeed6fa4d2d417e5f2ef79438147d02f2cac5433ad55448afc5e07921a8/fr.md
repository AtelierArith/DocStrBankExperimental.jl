```
<<(x, n)
```

Opérateur de décalage binaire à gauche, `x << n`. Pour `n >= 0`, le résultat est `x` décalé à gauche de `n` bits, rempli de `0`s. Cela équivaut à `x * 2^n`. Pour `n < 0`, cela équivaut à `x >> -n`.

# Exemples

```jldoctest
julia> Int8(3) << 2
12

julia> bitstring(Int8(3))
"00000011"

julia> bitstring(Int8(12))
"00001100"
```

Voir aussi [`>>`](@ref), [`>>>`](@ref), [`exp2`](@ref), [`ldexp`](@ref).
