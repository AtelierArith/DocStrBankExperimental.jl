```
mergewith(combine, d::AbstractDict, others::AbstractDict...)
mergewith(combine)
merge(combine, d::AbstractDict, others::AbstractDict...)
```

Construye una colección combinada a partir de las colecciones dadas. Si es necesario, los tipos de la colección resultante se promoverán para acomodar los tipos de las colecciones combinadas. Los valores con la misma clave se combinarán utilizando la función combinadora. La forma curried `mergewith(combine)` devuelve la función `(args...) -> mergewith(combine, args...)`.

El método `merge(combine::Union{Function,Type}, args...)` como un alias de `mergewith(combine, args...)` sigue disponible por compatibilidad hacia atrás.

!!! compat "Julia 1.5"
    `mergewith` requiere Julia 1.5 o posterior.


# Ejemplos

```jldoctest
julia> a = Dict("foo" => 0.0, "bar" => 42.0)
Dict{String, Float64} con 2 entradas:
  "bar" => 42.0
  "foo" => 0.0

julia> b = Dict("baz" => 17, "bar" => 4711)
Dict{String, Int64} con 2 entradas:
  "bar" => 4711
  "baz" => 17

julia> mergewith(+, a, b)
Dict{String, Float64} con 3 entradas:
  "bar" => 4753.0
  "baz" => 17.0
  "foo" => 0.0

julia> ans == mergewith(+)(a, b)
true
```
