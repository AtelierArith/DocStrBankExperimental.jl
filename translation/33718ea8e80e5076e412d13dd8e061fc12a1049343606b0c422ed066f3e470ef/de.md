```
Unsigned <: Integer
```

Abstrakte Oberklasse für alle unsigned Ganzzahlen.

Eingebaute unsigned Ganzzahlen werden in hexadezimaler Form mit dem Präfix `0x` ausgegeben und können auf die gleiche Weise eingegeben werden.

# Beispiele

```
julia> typemax(UInt8)
0xff

julia> Int(0x00d)
13

julia> unsigned(true)
0x0000000000000001
```
