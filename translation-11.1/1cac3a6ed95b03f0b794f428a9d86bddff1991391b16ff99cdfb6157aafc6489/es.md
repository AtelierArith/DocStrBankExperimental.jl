```
download(url::AbstractString, [path::AbstractString = tempname()]) -> path
```

Descarga un archivo de la URL dada, guardándolo en la ubicación `path`, o si no se especifica, en una ruta temporal. Devuelve la ruta del archivo descargado.

!!! note
    Desde Julia 1.6, esta función está en desuso y es solo un envoltorio delgado alrededor de `Downloads.download`. En el nuevo código, deberías usar esa función directamente en lugar de llamar a esta.

