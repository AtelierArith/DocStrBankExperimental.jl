```
unsafe_store!(p::Ptr{T}, x, i::Integer=1)
unsafe_store!(p::Ptr{T}, x, order::Symbol)
unsafe_store!(p::Ptr{T}, x, i::Integer, order::Symbol)
```

Almacena un valor del tipo `T` en la dirección del `i`-ésimo elemento (indexado desde 1) comenzando en `p`. Esto es equivalente a la expresión en C `p[i-1] = x`. Opcionalmente, se puede proporcionar un orden de memoria atómico.

El prefijo `unsafe` en esta función indica que no se realiza ninguna validación en el puntero `p` para asegurar que sea válido. Al igual que en C, el programador es responsable de asegurarse de que la memoria referenciada no se libere o recolecte mientras se invoca esta función. Un uso incorrecto puede causar un fallo de segmentación en tu programa. A diferencia de C, almacenar en una región de memoria asignada como un tipo diferente puede ser válido siempre que los tipos sean compatibles.

!!! compat "Julia 1.10"
    El argumento `order` está disponible a partir de Julia 1.10.


Ver también: [`atomic`](@ref)
