```
include_string([mapexpr::Function,] m::Module, code::AbstractString, filename::AbstractString="string")
```

Como [`include`](@ref), excepto que lee el código de la cadena dada en lugar de un archivo.

El primer argumento opcional `mapexpr` se puede usar para transformar el código incluido antes de que se evalúe: para cada expresión analizada `expr` en `code`, la función `include_string` evalúa en realidad `mapexpr(expr)`. Si se omite, `mapexpr` por defecto es [`identity`](@ref).

!!! compat "Julia 1.5"
    Se requiere Julia 1.5 para pasar el argumento `mapexpr`.

