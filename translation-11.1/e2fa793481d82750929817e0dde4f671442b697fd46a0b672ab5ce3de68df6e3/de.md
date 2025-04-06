```
isascii(cu::AbstractVector{CU}) where {CU <: Integer} -> Bool
```

Überprüfen, ob alle Werte im Vektor zum ASCII-Zeichensatz (0x00 bis 0x7f) gehören. Diese Funktion ist dazu gedacht, von anderen String-Implementierungen verwendet zu werden, die eine schnelle ASCII-Prüfung benötigen.
