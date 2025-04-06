```
stage(ie::IndexEntry) -> Cint
```

Obtiene el número de etapa de `ie`. El número de etapa `0` representa el estado actual del árbol de trabajo, pero se pueden usar otros números en caso de un conflicto de fusión. En tal caso, los diversos números de etapa en un `IndexEntry` describen a qué lado(s) del conflicto pertenece el estado actual del archivo. La etapa `0` es el estado antes de la fusión intentada, la etapa `1` son los cambios que se han realizado localmente, las etapas `2` y superiores son para cambios de otras ramas (por ejemplo, en el caso de una fusión "octopus" de múltiples ramas, se podrían usar las etapas `2`, `3` y `4`).
