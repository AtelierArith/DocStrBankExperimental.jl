```
hex2bytes!(dest::AbstractVector{UInt8}, itr)
```

Convertir un itérable `itr` d'octets représentant une chaîne hexadécimale en sa représentation binaire, similaire à [`hex2bytes`](@ref) sauf que la sortie est écrite en place dans `dest`. La longueur de `dest` doit être la moitié de la longueur de `itr`.

!!! compat "Julia 1.7"
    Appeler hex2bytes! avec des itérateurs produisant des UInt8 nécessite la version 1.7. Dans les versions antérieures, vous pouvez collecter l'itérable avant d'appeler à la place.

