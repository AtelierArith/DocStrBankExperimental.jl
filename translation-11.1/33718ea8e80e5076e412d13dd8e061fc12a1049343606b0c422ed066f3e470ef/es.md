```
Unsigned <: Integer
```

Supertipo abstracto para todos los enteros sin signo.

Los enteros sin signo incorporados se imprimen en hexadecimal, con el prefijo `0x`, y se pueden ingresar de la misma manera.

# Ejemplos

```
julia> typemax(UInt8)
0xff

julia> Int(0x00d)
13

julia> unsigned(true)
0x0000000000000001
```
