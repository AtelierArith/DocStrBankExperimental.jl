```
a ? b : c
```

Forma corta para condicionales; se lee "si `a`, evalúa `b` de lo contrario evalúa `c`". También conocido como el [operador ternario](https://en.wikipedia.org/wiki/%3F:).

Esta sintaxis es equivalente a `if a; b else c end`, pero a menudo se utiliza para enfatizar el valor `b`-o-`c` que se está utilizando como parte de una expresión más grande, en lugar de los efectos secundarios que la evaluación de `b` o `c` puede tener.

Consulta la sección del manual sobre [flujo de control](@ref man-conditional-evaluation) para más detalles.

# Ejemplos

```jldoctest
julia> x = 1; y = 2;

julia> x > y ? println("x es mayor") : println("x no es mayor")
x no es mayor

julia> x > y ? "x es mayor" : x == y ? "x e y son iguales" : "y es mayor"
"y es mayor"
```
