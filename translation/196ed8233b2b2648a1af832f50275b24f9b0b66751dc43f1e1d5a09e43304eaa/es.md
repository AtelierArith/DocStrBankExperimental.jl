```
typejoin(T, S, ...)
```

Devuelve el ancestro común más cercano de los tipos `T` y `S`, es decir, el tipo más estrecho del cual ambos heredan. Recurre en argumentos adicionales.

# Ejemplos

```jldoctest
julia> typejoin(Int, Float64)
Real

julia> typejoin(Int, Float64, ComplexF32)
Number
```
