```
find_library(nombres [, ubicaciones])
```

Busca la primera biblioteca en `nombres` en las rutas de la lista `ubicaciones`, `DL_LOAD_PATH` o rutas de bibliotecas del sistema (en ese orden) que se pueda abrir con éxito mediante dlopen. En caso de éxito, el valor de retorno será uno de los nombres (potencialmente precedido por una de las rutas en ubicaciones). Esta cadena se puede asignar a un `global const` y usarse como el nombre de la biblioteca en futuros `ccall`. En caso de fallo, devuelve la cadena vacía.
