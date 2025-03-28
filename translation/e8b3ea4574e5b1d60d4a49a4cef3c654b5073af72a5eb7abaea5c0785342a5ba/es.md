```
values(iterator)
```

Para un iterador o colección que tiene claves y valores, devuelve un iterador sobre los valores. Esta función simplemente devuelve su argumento por defecto, ya que los elementos de un iterador general se consideran normalmente sus "valores".

# Ejemplos

```jldoctest
julia> d = Dict("a"=>1, "b"=>2);

julia> values(d)
ValueIterator for a Dict{String, Int64} with 2 entries. Values:
  2
  1

julia> values([2])
1-element Vector{Int64}:
 2
```
