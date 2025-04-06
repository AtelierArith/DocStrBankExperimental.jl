```
LazyString <: AbstractString
```

Una representación perezosa de la interpolación de cadenas. Esto es útil cuando se necesita construir una cadena en un contexto donde realizar la interpolación real y la construcción de la cadena es innecesario o indeseable (por ejemplo, en rutas de error de funciones).

Este tipo está diseñado para ser barato de construir en tiempo de ejecución, tratando de descargar tanto trabajo como sea posible a la macro o a las operaciones de impresión posteriores.

# Ejemplos

```jldoctest
julia> n = 5; str = LazyString("n es ", n)
"n es 5"
```

Ver también [`@lazy_str`](@ref).

!!! compat "Julia 1.8"
    `LazyString` requiere Julia 1.8 o posterior.


# Ayuda extendida

## Propiedades de seguridad para programas concurrentes

Una cadena perezosa en sí misma no introduce ningún problema de concurrencia, incluso si se imprime en múltiples tareas de Julia. Sin embargo, si los métodos `print` sobre un valor capturado pueden tener un problema de concurrencia cuando se invocan sin sincronizaciones, imprimir la cadena perezosa puede causar un problema. Además, los métodos `print` sobre los valores capturados pueden ser invocados múltiples veces, aunque solo se devolverá exactamente un resultado.

!!! compat "Julia 1.9"
    `LazyString` es seguro en el sentido anterior en Julia 1.9 y versiones posteriores.

