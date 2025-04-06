```
Core.Type{T}
```

`Core.Type` es un tipo abstracto que tiene todos los objetos de tipo como sus instancias. La única instancia del tipo singleton `Core.Type{T}` es el objeto `T`.

# Ejemplos

```jldoctest
julia> isa(Type{Float64}, Type)
true

julia> isa(Float64, Type)
true

julia> isa(Real, Type{Float64})
false

julia> isa(Real, Type{Real})
true
```
