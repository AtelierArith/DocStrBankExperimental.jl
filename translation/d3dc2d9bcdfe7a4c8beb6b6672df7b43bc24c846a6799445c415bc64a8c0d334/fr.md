```
readbytes!(stream::IOStream, b::AbstractVector{UInt8}, nb=length(b); all::Bool=true)
```

Lit au maximum `nb` octets depuis `stream` dans `b`, retournant le nombre d'octets lus. La taille de `b` sera augmentée si nécessaire (c'est-à-dire si `nb` est supérieur à `length(b)` et que suffisamment d'octets ont pu être lus), mais elle ne sera jamais diminuée.

Si `all` est `true` (par défaut), cette fonction bloquera en essayant de lire tous les octets demandés, jusqu'à ce qu'une erreur ou la fin du fichier se produise. Si `all` est `false`, au maximum un appel à `read` est effectué, et la quantité de données retournées dépend du périphérique. Notez que tous les types de flux ne prennent pas en charge l'option `all`.
