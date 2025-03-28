```
UInt
```

Tipo de entero sin signo de Sys.WORD_SIZE bits, `UInt <: Unsigned <: Integer`.

Al igual que [`Int`](@ref Int), el alias `UInt` puede apuntar a `UInt32` o `UInt64`, según el valor de `Sys.WORD_SIZE` en una computadora dada.

Impreso y analizado en hexadecimal: `UInt(15) === 0x000000000000000f`.
