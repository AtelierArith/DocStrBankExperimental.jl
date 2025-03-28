```
include([mapexpr::Function,] path::AbstractString)
```

Evalúa el contenido del archivo de origen de entrada en el ámbito global del módulo que lo contiene. Cada módulo (excepto aquellos definidos con `baremodule`) tiene su propia definición de `include`, que evalúa el archivo en ese módulo. Devuelve el resultado de la última expresión evaluada del archivo de entrada. Durante la inclusión, se establece una ruta de inclusión local a la tarea en el directorio que contiene el archivo. Las llamadas anidadas a `include` buscarán en relación con esa ruta. Esta función se utiliza típicamente para cargar código fuente de forma interactiva, o para combinar archivos en paquetes que están divididos en múltiples archivos de origen. El argumento `path` se normaliza utilizando [`normpath`](@ref) que resolverá los tokens de ruta relativa como `..` y convertirá `/` en el separador de ruta apropiado.

El primer argumento opcional `mapexpr` se puede usar para transformar el código incluido antes de que se evalúe: para cada expresión analizada `expr` en `path`, la función `include` en realidad evalúa `mapexpr(expr)`. Si se omite, `mapexpr` por defecto es [`identity`](@ref).

Usa [`Base.include`](@ref) para evaluar un archivo en otro módulo.

!!! compat "Julia 1.5"
    Se requiere Julia 1.5 para pasar el argumento `mapexpr`.

