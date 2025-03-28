```
Core.Type{T}
```

`Core.Type` ist ein abstrakter Typ, der alle Typobjekte als seine Instanzen hat. Die einzige Instanz des Singleton-Typs `Core.Type{T}` ist das Objekt `T`.

# Beispiele

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
