```
Experimental.register_error_hint(handler, exceptiontype)
```

Registra una función de "sugerencia" `handler(io, exception)` que puede sugerir formas potenciales para que los usuarios eviten errores. `handler` debe examinar `exception` para ver si se cumplen las condiciones apropiadas para una sugerencia y, de ser así, generar salida a `io`. Los paquetes deben llamar a `register_error_hint` desde dentro de su función `__init__`.

Para tipos de excepciones específicos, se requiere que `handler` acepte argumentos adicionales:

  * `MethodError`: proporcionar `handler(io, exc::MethodError, argtypes, kwargs)`, que divide los argumentos combinados en argumentos posicionales y de palabra clave.

Al emitir una sugerencia, la salida debe comenzar típicamente con `\n`.

Si defines tipos de excepciones personalizados, tu método `showerror` puede soportar sugerencias llamando a [`Experimental.show_error_hints`](@ref).

# Ejemplos

```
julia> module Hinter

       only_int(x::Int)      = 1
       any_number(x::Number) = 2

       function __init__()
           Base.Experimental.register_error_hint(MethodError) do io, exc, argtypes, kwargs
               if exc.f == only_int
                    # El color no es necesario, esto es solo para mostrar que es posible.
                    print(io, "\n¿Quisiste llamar a ")
                    printstyled(io, "`any_number`?", color=:cyan)
               end
           end
       end

       end
```

Entonces, si llamas a `Hinter.only_int` con algo que no es un `Int` (activando así un `MethodError`), emite la sugerencia:

```
julia> Hinter.only_int(1.0)
ERROR: MethodError: no method matching only_int(::Float64)
La función `only_int` existe, pero no se define ningún método para esta combinación de tipos de argumento.
¿Quisiste llamar a `any_number`?
Los candidatos más cercanos son:
    ...
```

!!! compat "Julia 1.5"
    Las sugerencias de error personalizadas están disponibles a partir de Julia 1.5.


!!! warning
    Esta interfaz es experimental y está sujeta a cambios o eliminación sin previo aviso. Para protegerte contra cambios, considera poner cualquier registro dentro de un bloque `if isdefined(Base.Experimental, :register_error_hint) ... end`.

