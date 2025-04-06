```
bytes2hex(itr) -> String
bytes2hex(io::IO, itr)
```

Convertit un itérateur `itr` d'octets en sa représentation sous forme de chaîne hexadécimale, soit en retournant une `String` via `bytes2hex(itr)`, soit en écrivant la chaîne dans un flux `io` via `bytes2hex(io, itr)`.  Les caractères hexadécimaux sont tous en minuscules.

!!! compat "Julia 1.7"
    Appeler `bytes2hex` avec des itérateurs arbitraires produisant des valeurs `UInt8` nécessite Julia 1.7 ou une version ultérieure. Dans les versions antérieures, vous pouvez `collect` l'itérateur avant d'appeler `bytes2hex`.


# Exemples

```jldoctest
julia> a = string(12345, base = 16)
"3039"

julia> b = hex2bytes(a)
2-element Vector{UInt8}:
 0x30
 0x39

julia> bytes2hex(b)
"3039"
```
