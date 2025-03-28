```
readbytes!(stream::IO, b::AbstractVector{UInt8}, nb=length(b))
```

Lire au maximum `nb` octets depuis `stream` dans `b`, en retournant le nombre d'octets lus. La taille de `b` sera augmentée si nécessaire (c'est-à-dire si `nb` est supérieur à `length(b)` et que suffisamment d'octets ont pu être lus), mais elle ne sera jamais diminuée.
