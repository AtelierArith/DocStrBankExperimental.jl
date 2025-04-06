```
GC.gc([full=true])
```

Effectuez la collecte des ordures. L'argument `full` détermine le type de collecte : une collecte complète (par défaut) parcourt tous les objets vivants (c'est-à-dire un marquage complet) et devrait récupérer de la mémoire de tous les objets inaccessibles. Une collecte incrémentielle ne récupère de la mémoire que des jeunes objets qui ne sont pas accessibles.

Le GC peut décider d'effectuer une collecte complète même si une collecte incrémentielle a été demandée.

!!! avertissement
    Une utilisation excessive entraînera probablement une mauvaise performance.

