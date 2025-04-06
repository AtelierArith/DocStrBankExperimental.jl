```
cp(src::AbstractString, dst::AbstractString; force::Bool=false, follow_symlinks::Bool=false)
```

Copia el archivo, enlace o directorio de `src` a `dst`. `force=true` eliminará primero un `dst` existente.

Si `follow_symlinks=false`, y `src` es un enlace simbólico, `dst` se creará como un enlace simbólico. Si `follow_symlinks=true` y `src` es un enlace simbólico, `dst` será una copia del archivo o directorio al que se refiere `src`. Devuelve `dst`.

!!! note
    La función `cp` es diferente del comando `cp`. La función `cp` siempre opera bajo la suposición de que `dst` es un archivo, mientras que el comando hace cosas diferentes dependiendo de si `dst` es un directorio o un archivo. Usar `force=true` cuando `dst` es un directorio resultará en la pérdida de todo el contenido presente en el directorio `dst`, y `dst` se convertirá en un archivo que tiene el contenido de `src` en su lugar.

