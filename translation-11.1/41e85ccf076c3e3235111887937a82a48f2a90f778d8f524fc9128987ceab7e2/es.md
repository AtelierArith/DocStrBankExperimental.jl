```
merge(d::AbstractDict, others::AbstractDict...)
```

Construye una colección combinada a partir de las colecciones dadas. Si es necesario, los tipos de la colección resultante se promoverán para acomodar los tipos de las colecciones combinadas. Si la misma clave está presente en otra colección, el valor para esa clave será el valor que tiene en la última colección listada. Véase también [`mergewith`](@ref) para el manejo personalizado de valores con la misma clave.

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

julia> merge(a, b)
Dict{String, Float64} con 3 entradas:
  "bar" => 4711.0
  "baz" => 17.0
  "foo" => 0.0

julia> merge(b, a)
Dict{String, Float64} con 3 entradas:
  "bar" => 42.0
  "baz" => 17.0
  "foo" => 0.0
```
