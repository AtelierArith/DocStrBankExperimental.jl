```
poll_file(path::AbstractString, interval_s::Real=5.007, timeout_s::Real=-1) -> (previous::StatStruct, current)
```

Surveillez un fichier pour détecter des changements en interrogeant toutes les `interval_s` secondes jusqu'à ce qu'un changement se produise ou que `timeout_s` secondes se soient écoulées. L'`interval_s` doit être une longue période ; la valeur par défaut est de 5.007 secondes.

Renvoie une paire d'objets d'état `(previous, current)` lorsqu'un changement est détecté. L'état `previous` est toujours un `StatStruct`, mais il peut avoir tous les champs à zéro (indiquant que le fichier n'existait pas auparavant ou n'était pas accessible auparavant).

L'objet d'état `current` peut être un `StatStruct`, une `EOFError` (indiquant que le délai a expiré), ou un autre sous-type d'`Exception` (si l'opération `stat` a échoué - par exemple, si le chemin n'existe pas).

Pour déterminer quand un fichier a été modifié, comparez `current isa StatStruct && mtime(prev) != mtime(current)` pour détecter la notification de changements. Cependant, l'utilisation de [`watch_file`](@ref) pour cette opération est préférable, car elle est plus fiable et efficace, bien que dans certaines situations, elle puisse ne pas être disponible.
