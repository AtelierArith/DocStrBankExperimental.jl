```
@assert cond [texto]
```

Lanza un [`AssertionError`](@ref) si `cond` es `false`. Esta es la sintaxis preferida para escribir afirmaciones, que son condiciones que se asumen como verdaderas, pero que el usuario podría decidir verificar de todos modos, como una ayuda para la depuración si fallan. El mensaje opcional `texto` se muestra al fallar la afirmación.

!!! warning
    Una afirmación podría estar deshabilitada en algunos niveles de optimización. Por lo tanto, las afirmaciones solo deben usarse como una herramienta de depuración y no deben usarse para la verificación de autenticación (por ejemplo, verificar contraseñas o comprobar límites de arreglos). El código no debe depender de los efectos secundarios de ejecutar `cond` para el comportamiento correcto de una función.


# Ejemplos

```jldoctest
julia> @assert iseven(3) "¡3 es un número impar!"
ERROR: AssertionError: 3 es un número impar!

julia> @assert isodd(3) "¿Qué son los números pares?"
```
