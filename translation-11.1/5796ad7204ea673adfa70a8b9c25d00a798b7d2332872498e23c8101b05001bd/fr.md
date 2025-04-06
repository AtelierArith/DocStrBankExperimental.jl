```
UInt
```

Type entier non signé de taille `Sys.WORD_SIZE` bits, `UInt <: Unsigned <: Integer`.

Comme [`Int`](@ref Int), l'alias `UInt` peut pointer soit vers `UInt32` soit vers `UInt64`, selon la valeur de `Sys.WORD_SIZE` sur un ordinateur donné.

Imprimé et analysé en hexadécimal : `UInt(15) === 0x000000000000000f`.
