```
partialsortperm!(ix, v, k; by=identity, lt=isless, rev=false)
```

Como [`partialsortperm`](@ref), pero acepta un vector de índices `ix` preasignado del mismo tamaño que `v`, que se utiliza para almacenar (una permutación de) los índices de `v`.

`ix` se inicializa para contener los índices de `v`.

(Típicamente, los índices de `v` serán `1:length(v)`, aunque si `v` tiene un tipo de arreglo alternativo con índices que no comienzan en uno, como un `OffsetArray`, `ix` debe compartir esos mismos índices)

Al regresar, se garantiza que `ix` tendrá los índices `k` en sus posiciones ordenadas, de modo que

```julia
partialsortperm!(ix, v, k);
v[ix[k]] == partialsort(v, k)
```

El valor de retorno es el `k`-ésimo elemento de `ix` si `k` es un entero, o una vista en `ix` si `k` es un rango.

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


# Ejemplos

```jldoctest
julia> v = [3, 1, 2, 1];

julia> ix = Vector{Int}(undef, 4);

julia> partialsortperm!(ix, v, 1)
2

julia> ix = [1:4;];

julia> partialsortperm!(ix, v, 2:3)
2-element view(::Vector{Int64}, 2:3) with eltype Int64:
 4
 3
```

```
