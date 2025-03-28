```
copyto!(dest::AbstractArray, src) -> dest
```

Copia todos los elementos de la colección `src` al array `dest`, cuya longitud debe ser mayor o igual a la longitud `n` de `src`. Los primeros `n` elementos de `dest` son sobrescritos, los otros elementos permanecen intactos.

Véase también [`copy!`](@ref Base.copy!), [`copy`](@ref).

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


# Ejemplos

```jldoctest
julia> x = [1., 0., 3., 0., 5.];

julia> y = zeros(7);

julia> copyto!(y, x);

julia> y
7-element Vector{Float64}:
 1.0
 0.0
 3.0
 0.0
 5.0
 0.0
 0.0
```
