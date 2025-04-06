```
isconcretetype(T)
```

Determina si el tipo `T` es un tipo concreto, lo que significa que podría tener instancias directas (valores `x` tales que `typeof(x) === T`). Ten en cuenta que esto no es la negación de `isabstracttype(T)`. Si `T` no es un tipo, entonces devuelve `false`.

Ver también: [`isbits`](@ref), [`isabstracttype`](@ref), [`issingletontype`](@ref).

# Ejemplos

```jldoctest
julia> isconcretetype(Complex)
false

julia> isconcretetype(Complex{Float32})
true

julia> isconcretetype(Vector{Complex})
true

julia> isconcretetype(Vector{Complex{Float32}})
true

julia> isconcretetype(Union{})
false

julia> isconcretetype(Union{Int,String})
false
```
