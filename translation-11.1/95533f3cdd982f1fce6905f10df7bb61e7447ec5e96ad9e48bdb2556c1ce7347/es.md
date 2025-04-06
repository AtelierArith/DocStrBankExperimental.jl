```
rethrow()
```

Vuelve a lanzar la excepción actual desde dentro de un bloque `catch`. La excepción relanzada continuará propagándose como si no hubiera sido capturada.

!!! note
    La forma alternativa `rethrow(e)` te permite asociar un objeto de excepción alternativo `e` con la traza de pila actual. Sin embargo, esto tergiversa el estado del programa en el momento del error, por lo que se te anima a lanzar una nueva excepción usando `throw(e)`. En Julia 1.1 y versiones posteriores, usar `throw(e)` preservará la excepción raíz en la pila, como se describe en [`current_exceptions`](@ref).

