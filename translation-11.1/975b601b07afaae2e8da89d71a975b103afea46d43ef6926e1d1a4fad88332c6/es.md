```
Base.include([mapexpr::Function,] m::Module, path::AbstractString)
```

Evalúa el contenido del archivo de origen de entrada en el ámbito global del módulo `m`. Cada módulo (excepto aquellos definidos con [`baremodule`](@ref)) tiene su propia definición de `include` omitiendo el argumento `m`, que evalúa el archivo en ese módulo. Devuelve el resultado de la última expresión evaluada del archivo de entrada. Durante la inclusión, se establece una ruta de inclusión local a la tarea en el directorio que contiene el archivo. Las llamadas anidadas a `include` buscarán en relación con esa ruta. Esta función se utiliza típicamente para cargar código fuente de forma interactiva, o para combinar archivos en paquetes que están divididos en múltiples archivos de origen.

El primer argumento opcional `mapexpr` se puede usar para transformar el código incluido antes de que se evalúe: para cada expresión analizada `expr` en `path`, la función `include` en realidad evalúa `mapexpr(expr)`. Si se omite, `mapexpr` por defecto es [`identity`](@ref).

!!! compat "Julia 1.5"
    Se requiere Julia 1.5 para pasar el argumento `mapexpr`.

