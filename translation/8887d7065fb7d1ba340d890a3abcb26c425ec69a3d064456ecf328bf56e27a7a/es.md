```
@kwdef typedef
```

Este es un macro auxiliar que define automáticamente un constructor basado en palabras clave para el tipo declarado en la expresión `typedef`, que debe ser una expresión de `struct` o `mutable struct`. El argumento predeterminado se proporciona declarando campos de la forma `field::T = default` o `field = default`. Si no se proporciona un valor predeterminado, entonces el argumento de palabra clave se convierte en un argumento de palabra clave requerido en el constructor de tipo resultante.

Los constructores internos aún se pueden definir, pero al menos uno debe aceptar argumentos en la misma forma que el constructor interno predeterminado (es decir, un argumento posicional por campo) para funcionar correctamente con el constructor externo de palabras clave.

!!! compat "Julia 1.1"
    `Base.@kwdef` para structs paramétricos y structs con supertipos requiere al menos Julia 1.1.


!!! compat "Julia 1.9"
    Este macro se exporta a partir de Julia 1.9.


# Ejemplos

```jldoctest
julia> @kwdef struct Foo
           a::Int = 1         # valor predeterminado especificado
           b::String          # palabra clave requerida
       end
Foo

julia> Foo(b="hi")
Foo(1, "hi")

julia> Foo()
ERROR: UndefKeywordError: argumento de palabra clave `b` no asignado
Stacktrace:
[...]
```
