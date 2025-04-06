```
isabstracttype(T)
```

Determina si el tipo `T` fue declarado como un tipo abstracto (es decir, utilizando la sintaxis `abstract type`). Ten en cuenta que esto no es la negación de `isconcretetype(T)`. Si `T` no es un tipo, entonces devuelve `false`.

# Ejemplos

```jldoctest
julia> isabstracttype(AbstractArray)
true

julia> isabstracttype(Vector)
false
```
