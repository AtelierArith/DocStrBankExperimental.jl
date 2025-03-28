```
relpath(path::AbstractString, startpath::AbstractString = ".") -> String
```

Devuelve una ruta de archivo relativa a `path` ya sea desde el directorio actual o desde un directorio de inicio opcional. Este es un cálculo de ruta: no se accede al sistema de archivos para confirmar la existencia o naturaleza de `path` o `startpath`.

En Windows, la sensibilidad a mayúsculas y minúsculas se aplica a cada parte de la ruta, excepto a las letras de unidad. Si `path` y `startpath` se refieren a diferentes unidades, se devuelve la ruta absoluta de `path`.
