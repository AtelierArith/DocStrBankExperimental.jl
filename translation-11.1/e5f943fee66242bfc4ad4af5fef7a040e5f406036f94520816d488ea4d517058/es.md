```
abspath(path::AbstractString) -> String
```

Convierte una ruta a una ruta absoluta añadiendo el directorio actual si es necesario. También normaliza la ruta como en [`normpath`](@ref).

# Ejemplos

Si estás en un directorio llamado `JuliaExample` y los datos que estás utilizando están dos niveles arriba en relación con el directorio `JuliaExample`, podrías escribir:

```
abspath("../../data")
```

Lo que da una ruta como `"/home/JuliaUser/data/"`.

Consulta también [`joinpath`](@ref), [`pwd`](@ref), [`expanduser`](@ref).
