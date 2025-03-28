```
elsize(tipo)
```

Calcula el paso de memoria en bytes entre elementos consecutivos de [`eltype`](@ref) almacenados dentro del `tipo` dado, si los elementos del arreglo se almacenan de manera densa con un paso lineal uniforme.

# Ejemplos

```jldoctest
julia> Base.elsize(rand(Float32, 10))
4
```
