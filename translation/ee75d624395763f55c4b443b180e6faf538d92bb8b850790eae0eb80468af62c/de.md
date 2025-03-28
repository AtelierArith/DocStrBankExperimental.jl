```
hasfield(T::Type, name::Symbol)
```

Gibt einen Booleschen Wert zurück, der angibt, ob `T` `name` als eines seiner eigenen Felder hat.

Siehe auch [`fieldnames`](@ref), [`fieldcount`](@ref), [`hasproperty`](@ref).

!!! compat "Julia 1.2"
    Diese Funktion erfordert mindestens Julia 1.2.


# Beispiele

```jldoctest
julia> struct Foo
            bar::Int
       end

julia> hasfield(Foo, :bar)
true

julia> hasfield(Foo, :x)
false
```
