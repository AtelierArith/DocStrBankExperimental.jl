```
hasfield(T::Type, name::Symbol)
```

Devuelve un booleano que indica si `T` tiene `name` como uno de sus propios campos.

Véase también [`fieldnames`](@ref), [`fieldcount`](@ref), [`hasproperty`](@ref).

!!! compat "Julia 1.2"
    Esta función requiere al menos Julia 1.2.


# Ejemplos

```jldoctest
julia> struct Foo
            bar::Int
       end

julia> hasfield(Foo, :bar)
true

julia> hasfield(Foo, :x)
false
```
