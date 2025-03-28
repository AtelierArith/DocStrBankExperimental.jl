```
isascii(cu::AbstractVector{CU}) where {CU <: Integer} -> Bool
```

Prueba si todos los valores en el vector pertenecen al conjunto de caracteres ASCII (0x00 a 0x7f). Esta función está destinada a ser utilizada por otras implementaciones de cadenas que necesitan una verificación rápida de ASCII.
