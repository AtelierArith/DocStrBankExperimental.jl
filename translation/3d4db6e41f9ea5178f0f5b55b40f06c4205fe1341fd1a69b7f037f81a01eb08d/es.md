```
count([f=identity,] itr; init=0) -> Integer
```

Cuenta el número de elementos en `itr` para los cuales la función `f` devuelve `true`. Si se omite `f`, cuenta el número de elementos `true` en `itr` (que debe ser una colección de valores booleanos). `init` especifica opcionalmente el valor desde el cual comenzar a contar y, por lo tanto, también determina el tipo de salida.

!!! compat "Julia 1.6"
    La palabra clave `init` se agregó en Julia 1.6.


Véase también: [`any`](@ref), [`sum`](@ref).

# Ejemplos

```jldoctest
julia> count(i->(4<=i<=6), [2,3,4,5,6])
3

julia> count([true, false, true, true])
3

julia> count(>(3), 1:7, init=0x03)
0x07
```
