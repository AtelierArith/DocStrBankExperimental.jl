```
UInt
```

Sys.WORD_SIZE-Bit unsigned Integer-Typ, `UInt <: Unsigned <: Integer`.

Wie [`Int`](@ref Int) kann das Alias `UInt` entweder auf `UInt32` oder `UInt64` verweisen, je nach dem Wert von `Sys.WORD_SIZE` auf einem bestimmten Computer.

Gedruckt und geparst in Hexadezimal: `UInt(15) === 0x000000000000000f`.
