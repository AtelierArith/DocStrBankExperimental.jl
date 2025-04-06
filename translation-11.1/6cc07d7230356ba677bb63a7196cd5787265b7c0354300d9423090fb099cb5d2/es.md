```
unsafe_convert(T, x)
```

Convierte `x` a un argumento C de tipo `T` donde la entrada `x` debe ser el valor de retorno de `cconvert(T, ...)`.

En los casos donde [`convert`](@ref) necesitaría tomar un objeto de Julia y convertirlo en un `Ptr`, esta función debe ser utilizada para definir y realizar esa conversión.

Ten cuidado de asegurarte de que una referencia de Julia a `x` exista mientras se utilice el resultado de esta función. En consecuencia, el argumento `x` para esta función nunca debe ser una expresión, solo un nombre de variable o referencia de campo. Por ejemplo, `x=a.b.c` es aceptable, pero `x=[a,b,c]` no lo es.

El prefijo `unsafe` en esta función indica que usar el resultado de esta función después de que el argumento `x` de esta función ya no sea accesible para el programa puede causar un comportamiento indefinido, incluyendo corrupción del programa o segfaults, en cualquier momento posterior.

Ver también [`cconvert`](@ref)
