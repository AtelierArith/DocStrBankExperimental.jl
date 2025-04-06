```
@uint128_str str
```

Analyse `str` comme un [`UInt128`](@ref). Lancez une `ArgumentError` si la chaîne n'est pas un entier valide.

# Exemples

```
julia> uint128"123456789123"
0x00000000000000000000001cbe991a83

julia> uint128"-123456789123"
ERROR: LoadError: ArgumentError: invalid base 10 digit '-' in "-123456789123"
[...]
```
