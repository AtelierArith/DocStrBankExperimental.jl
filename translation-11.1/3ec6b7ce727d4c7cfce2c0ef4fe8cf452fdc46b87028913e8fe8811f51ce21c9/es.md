```
mergewith!(combine, d::AbstractDict, others::AbstractDict...) -> d
mergewith!(combine)
merge!(combine, d::AbstractDict, others::AbstractDict...) -> d
```

Actualiza la colección con pares de las otras colecciones. Los valores con la misma clave se combinarán utilizando la función combinadora. La forma curried `mergewith!(combine)` devuelve la función `(args...) -> mergewith!(combine, args...)`.

El método `merge!(combine::Union{Function,Type}, args...)` como un alias de `mergewith!(combine, args...)` sigue disponible por compatibilidad hacia atrás.

!!! compat "Julia 1.5"
    `mergewith!` requiere Julia 1.5 o posterior.


# Ejemplos

```jldoctest
julia> d1 = Dict(1 => 2, 3 => 4);

julia> d2 = Dict(1 => 4, 4 => 5);

julia> mergewith!(+, d1, d2);

julia> d1
Dict{Int64, Int64} con 3 entradas:
  4 => 5
  3 => 4
  1 => 6

julia> mergewith!(-, d1, d1);

julia> d1
Dict{Int64, Int64} con 3 entradas:
  4 => 0
  3 => 0
  1 => 0

julia> foldl(mergewith!(+), [d1, d2]; init=Dict{Int64, Int64}())
Dict{Int64, Int64} con 3 entradas:
  4 => 5
  3 => 0
  1 => 4
```
