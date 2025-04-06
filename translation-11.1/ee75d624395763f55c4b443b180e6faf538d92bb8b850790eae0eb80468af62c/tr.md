```
hasfield(T::Type, name::Symbol)
```

`T`'nin `name` adında kendi alanlarından birine sahip olup olmadığını belirten bir boolean döndürür.

Ayrıca bkz. [`fieldnames`](@ref), [`fieldcount`](@ref), [`hasproperty`](@ref).

!!! compat "Julia 1.2"
    Bu fonksiyon en az Julia 1.2'yi gerektirir.


# Örnekler

```jldoctest
julia> struct Foo
            bar::Int
       end

julia> hasfield(Foo, :bar)
true

julia> hasfield(Foo, :x)
false
```
