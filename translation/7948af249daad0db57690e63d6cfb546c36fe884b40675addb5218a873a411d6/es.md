```
unsafe_load(p::Ptr{T}, i::Integer=1)
unsafe_load(p::Ptr{T}, order::Symbol)
unsafe_load(p::Ptr{T}, i::Integer, order::Symbol)
```

Carga un valor del tipo `T` desde la dirección del elemento `i` (indexado desde 1) comenzando en `p`. Esto es equivalente a la expresión en C `p[i-1]`. Opcionalmente, se puede proporcionar un orden de memoria atómico.

El prefijo `unsafe` en esta función indica que no se realiza ninguna validación en el puntero `p` para asegurar que sea válido. Al igual que en C, el programador es responsable de asegurarse de que la memoria referenciada no se libere o se recoja como basura mientras se invoca esta función. Un uso incorrecto puede causar un fallo de segmentación en tu programa o devolver respuestas incorrectas. A diferencia de C, desreferenciar una región de memoria asignada como un tipo diferente puede ser válido siempre que los tipos sean compatibles.

!!! compat "Julia 1.10"
    El argumento `order` está disponible a partir de Julia 1.10.


Ver también: [`atomic`](@ref)
