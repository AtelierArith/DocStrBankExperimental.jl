```
hex2bytes(itr)
```

Étant donné un itérable `itr` de codes ASCII pour une séquence de chiffres hexadécimaux, renvoie un `Vector{UInt8}` d'octets correspondant à la représentation binaire : chaque paire successive de chiffres hexadécimaux dans `itr` donne la valeur d'un octet dans le vecteur de retour.

La longueur de `itr` doit être paire, et le tableau retourné a la moitié de la longueur de `itr`. Voir aussi [`hex2bytes!`](@ref) pour une version en place, et [`bytes2hex`](@ref) pour l'inverse.

!!! compat "Julia 1.7"
    Appeler `hex2bytes` avec des itérateurs produisant des valeurs `UInt8` nécessite Julia 1.7 ou une version ultérieure. Dans les versions antérieures, vous pouvez `collect` l'itérateur avant d'appeler `hex2bytes`.


# Exemples

```jldoctest
julia> s = string(12345, base = 16)
"3039"

julia> hex2bytes(s)
2-element Vector{UInt8}:
 0x30
 0x39

julia> a = b"01abEF"
6-element Base.CodeUnits{UInt8, String}:
 0x30
 0x31
 0x61
 0x62
 0x45
 0x46

julia> hex2bytes(a)
3-element Vector{UInt8}:
 0x01
 0xab
 0xef
```
