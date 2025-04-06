```
@uint128_str str
```

Analysiere `str` als ein [`UInt128`](@ref). Wirf einen `ArgumentError`, wenn der String keine gültige Ganzzahl ist.

# Beispiele

```
julia> uint128"123456789123"
0x00000000000000000000001cbe991a83

julia> uint128"-123456789123"
ERROR: LoadError: ArgumentError: ungültige Basis 10 Ziffer '-' in "-123456789123"
[...]
```
