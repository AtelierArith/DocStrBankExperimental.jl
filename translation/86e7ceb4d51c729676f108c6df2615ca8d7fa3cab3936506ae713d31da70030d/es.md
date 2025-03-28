```
retrieve(; kwargs...) -> data, lidict
```

"Exports" los resultados de perfilado en un formato portátil, devolviendo el conjunto de todas las trazas de retroceso (`data`) y un diccionario que mapea los punteros de instrucción (específicos de la sesión) en `data` a valores de `LineInfo` que almacenan el nombre del archivo, el nombre de la función y el número de línea. Esta función te permite guardar los resultados de perfilado para un análisis futuro.
