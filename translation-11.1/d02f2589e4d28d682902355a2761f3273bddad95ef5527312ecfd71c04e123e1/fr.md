```
@b_str
```

Créez un vecteur d'octets immuable (`UInt8`) en utilisant la syntaxe de chaîne.

# Exemples

```jldoctest
julia> v = b"12\x01\x02"
4-element Base.CodeUnits{UInt8, String}:
 0x31
 0x32
 0x01
 0x02

julia> v[2]
0x32
```
