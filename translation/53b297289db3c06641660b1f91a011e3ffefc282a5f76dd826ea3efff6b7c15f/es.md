```
Base.rest(collection[, itr_state])
```

Función genérica para tomar la cola de `collection`, comenzando desde un estado de iteración específico `itr_state`. Devuelve un `Tuple`, si `collection` es un `Tuple`, un subtipo de `AbstractVector`, si `collection` es un `AbstractArray`, un subtipo de `AbstractString` si `collection` es un `AbstractString`, y un iterador arbitrario, recurriendo a `Iterators.rest(collection[, itr_state])`, de lo contrario.

Se puede sobrecargar para tipos de colección definidos por el usuario para personalizar el comportamiento de [slurping in assignments](@ref destructuring-assignment) en la posición final, como `a, b... = collection`.

!!! compat "Julia 1.6"
    `Base.rest` requiere al menos Julia 1.6.


Véase también: [`first`](@ref first), [`Iterators.rest`](@ref), [`Base.split_rest`](@ref).

# Ejemplos

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> first, state = iterate(a)
(1, 2)

julia> first, Base.rest(a, state)
(1, [3, 2, 4])
```
