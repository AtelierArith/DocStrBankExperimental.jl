```
ParserError
```

Tipo que se devuelve de [`tryparse`](@ref) y [`tryparsefile`](@ref) cuando el análisis falla. Contiene (entre otros) los siguientes campos:

  * `pos`, la posición en la cadena cuando ocurrió el error
  * `table`, el resultado que hasta ahora se ha analizado con éxito
  * `type`, un tipo de error, diferente para diferentes tipos de errores
