```
get!(f::Union{Function, Type}, collection, key)
```

Devuelve el valor almacenado para la clave dada, o si no hay un mapeo para la clave, almacena `key => f()`, y devuelve `f()`.

Esto está destinado a ser llamado utilizando la sintaxis de bloque `do`.

# Ejemplos

```jldoctest
julia> squares = Dict{Int, Int}();

julia> function get_square!(d, i)
           get!(d, i) do
               i^2
           end
       end
get_square! (generic function with 1 method)

julia> get_square!(squares, 2)
4

julia> squares
Dict{Int64, Int64} with 1 entry:
  2 => 4
```
