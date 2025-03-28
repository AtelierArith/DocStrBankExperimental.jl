```
randcycle!([rng=default_rng(),] A::Array{<:Integer})
```

Construye en `A` una permutación cíclica aleatoria de longitud `n = length(A)`. El argumento opcional `rng` especifica un generador de números aleatorios, consulta [Números Aleatorios](@ref).

Aquí, una "permutación cíclica" significa que todos los elementos se encuentran dentro de un solo ciclo. Si `A` no está vacío (`n > 0`), hay $(n-1)!$ posibles permutaciones cíclicas, que se muestrean de manera uniforme. Si `A` está vacío, `randcycle!` lo deja sin cambios.

[`randcycle`](@ref) es una variante de esta función que asigna un nuevo vector.

# Ejemplos

```jldoctest
julia> randcycle!(Xoshiro(123), Vector{Int}(undef, 6))
6-element Vector{Int64}:
 5
 4
 2
 6
 3
 1
```
