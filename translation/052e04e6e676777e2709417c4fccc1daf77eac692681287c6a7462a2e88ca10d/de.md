```
@int128_str str
```

Analysiere `str` als einen [`Int128`](@ref). Wirf einen `ArgumentError`, wenn der String keine gültige Ganzzahl ist.

# Beispiele

```jldoctest
julia> int128"123456789123"
123456789123

julia> int128"123456789123.4"
ERROR: LoadError: ArgumentError: ungültige Basis-10-Ziffer '.' in "123456789123.4"
[...]
```
