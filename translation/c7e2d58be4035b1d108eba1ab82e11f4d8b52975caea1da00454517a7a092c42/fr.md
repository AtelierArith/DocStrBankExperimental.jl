```
read(s::IOStream, nb::Integer; all=true)
```

Lire au maximum `nb` octets de `s`, renvoyant un `Vector{UInt8}` des octets lus.

Si `all` est `true` (la valeur par défaut), cette fonction bloquera en essayant de lire tous les octets demandés, jusqu'à ce qu'une erreur ou la fin du fichier se produise. Si `all` est `false`, au maximum un appel à `read` est effectué, et la quantité de données renvoyées dépend du périphérique. Notez que tous les types de flux ne prennent pas en charge l'option `all`.
