```
@cfunction(callable, ReturnType, (ArgumentTypes...,)) -> Ptr{Cvoid}
@cfunction($callable, ReturnType, (ArgumentTypes...,)) -> CFunction
```

Genera un puntero de función llamable en C a partir de la función de Julia `callable` para la firma de tipo dada. Para pasar el valor de retorno a un `ccall`, utiliza el tipo de argumento `Ptr{Cvoid}` en la firma.

Ten en cuenta que la tupla de tipos de argumento debe ser una tupla literal, y no una variable o expresión de tupla (aunque puede incluir una expresión de splat). Y que estos argumentos se evaluarán en el ámbito global durante el tiempo de compilación (no se diferirán hasta el tiempo de ejecución). Agregar un '$' delante del argumento de la función cambia esto para crear en su lugar un cierre en tiempo de ejecución sobre la variable local `callable` (esto no es compatible con todas las arquitecturas).

Consulta [la sección del manual sobre el uso de ccall y cfunction](@ref Calling-C-and-Fortran-Code).

# Ejemplos

```julia-repl
julia> function foo(x::Int, y::Int)
           return x + y
       end

julia> @cfunction(foo, Int, (Int, Int))
Ptr{Cvoid} @0x000000001b82fcd0
```
