```
SubArray{T,N,P,I,L} <: AbstractArray{T,N}
```

Vista `N`-dimensional en un array padre (de tipo `P`) con un tipo de elemento `T`, restringida por una tupla de índices (de tipo `I`). `L` es verdadero para tipos que soportan indexación lineal rápida, y falso en caso contrario.

Construya `SubArray`s utilizando la función [`view`](@ref).
