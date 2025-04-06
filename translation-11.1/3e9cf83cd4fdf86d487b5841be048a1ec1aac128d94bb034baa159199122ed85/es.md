```
sum(f, itr; [init])
```

Suma los resultados de llamar a la función `f` en cada elemento de `itr`.

El tipo de retorno es `Int` para enteros con signo de menos del tamaño de palabra del sistema, y `UInt` para enteros sin signo de menos del tamaño de palabra del sistema. Para todos los demás argumentos, se encuentra un tipo de retorno común al que se promueven todos los argumentos.

El valor devuelto para `itr` vacío puede ser especificado por `init`. Debe ser la identidad aditiva (es decir, cero) ya que no está especificado si `init` se utiliza para colecciones no vacías.

!!! compat "Julia 1.6"
    El argumento clave `init` requiere Julia 1.6 o posterior.


# Ejemplos

```jldoctest
julia> sum(abs2, [2; 3; 4])
29
```

Nota la importante diferencia entre `sum(A)` y `reduce(+, A)` para arreglos con un tipo de elemento entero pequeño:

```jldoctest
julia> sum(Int8[100, 28])
128

julia> reduce(+, Int8[100, 28])
-128
```

En el primer caso, los enteros se amplían al tamaño de palabra del sistema y, por lo tanto, el resultado es 128. En el segundo caso, no ocurre tal ampliación y el desbordamiento de enteros resulta en -128.
