```
Char(c::Union{Number,AbstractChar})
```

`Char` ist ein 32-Bit [`AbstractChar`](@ref) Typ, der die Standarddarstellung von Zeichen in Julia ist. `Char` ist der Typ, der für Zeichenliterale wie `'x'` verwendet wird, und es ist auch der Elementtyp von [`String`](@ref).

Um beliebige Byte-Streams, die in einem `String` gespeichert sind, verlustfrei darzustellen, kann ein `Char`-Wert Informationen speichern, die nicht in einen Unicode-Codepunkt konvertiert werden können — die Umwandlung eines solchen `Char` in `UInt32` wird einen Fehler auslösen. Die Funktion [`isvalid(c::Char)`](@ref) kann verwendet werden, um zu überprüfen, ob `c` ein gültiges Unicode-Zeichen darstellt.
