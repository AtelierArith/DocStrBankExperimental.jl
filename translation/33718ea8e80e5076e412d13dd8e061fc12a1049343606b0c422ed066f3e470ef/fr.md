```
Unsigned <: Integer
```

Supertype abstrait pour tous les entiers non signés.

Les entiers non signés intégrés sont imprimés en hexadécimal, avec le préfixe `0x`, et peuvent être saisis de la même manière.

# Exemples

```
julia> typemax(UInt8)
0xff

julia> Int(0x00d)
13

julia> unsigned(true)
0x0000000000000001
```
