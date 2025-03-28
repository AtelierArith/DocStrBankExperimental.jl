```
unsafe_wrap(Array, pointer::Ptr{T}, dims; own = false)
```

Envuelve un objeto `Array` de Julia alrededor de los datos en la dirección dada por `pointer`, sin hacer una copia. El tipo de elemento del puntero `T` determina el tipo de elemento del array. `dims` es un entero (para un array unidimensional) o una tupla de las dimensiones del array. `own` especifica opcionalmente si Julia debe tomar posesión de la memoria, llamando a `free` en el puntero cuando el array ya no esté referenciado.

Esta función está etiquetada como "insegura" porque se bloqueará si `pointer` no es una dirección de memoria válida para datos de la longitud solicitada. A diferencia de [`unsafe_load`](@ref) y [`unsafe_store!`](@ref), el programador también es responsable de asegurarse de que los datos subyacentes no se accedan a través de dos arrays de diferentes tipos de elementos, similar a la regla de aliasing estricto en C.
