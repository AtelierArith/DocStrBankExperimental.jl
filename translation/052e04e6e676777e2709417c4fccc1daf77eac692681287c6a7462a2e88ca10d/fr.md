```
@int128_str str
```

Analyse `str` comme un [`Int128`](@ref). Lancez une `ArgumentError` si la chaîne n'est pas un entier valide.

# Exemples

```jldoctest
julia> int128"123456789123"
123456789123

julia> int128"123456789123.4"
ERROR: LoadError: ArgumentError: invalid base 10 digit '.' in "123456789123.4"
[...]
```
