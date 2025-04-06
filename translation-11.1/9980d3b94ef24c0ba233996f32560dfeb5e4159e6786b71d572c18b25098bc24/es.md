```
axes(A, d)
```

Devuelve el rango válido de índices para el arreglo `A` a lo largo de la dimensión `d`.

Véase también [`size`](@ref), y el capítulo del manual sobre [arreglos con índices personalizados](@ref man-custom-indices).

# Ejemplos

```jldoctest
julia> A = fill(1, (5,6,7));

julia> axes(A, 2)
Base.OneTo(6)

julia> axes(A, 4) == 1:1  # todas las dimensiones d > ndims(A) tienen tamaño 1
true
```

# Nota de uso

Cada uno de los índices tiene que ser un `AbstractUnitRange{<:Integer}`, pero al mismo tiempo puede ser un tipo que use índices personalizados. Así que, por ejemplo, si necesitas un subconjunto, utiliza construcciones de indexación generalizadas como `begin`/`end` o [`firstindex`](@ref)/[`lastindex`](@ref):

```julia
ix = axes(v, 1)
ix[2:end]          # funcionará para por ejemplo Vector, pero puede fallar en general
ix[(begin+1):end]  # funciona para índices generalizados
```
