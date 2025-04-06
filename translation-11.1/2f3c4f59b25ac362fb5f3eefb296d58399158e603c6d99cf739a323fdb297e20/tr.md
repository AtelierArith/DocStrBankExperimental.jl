```
Core.Type{T}
```

`Core.Type` tüm tür nesnelerinin örnekleri olan soyut bir türdür. Tekil tür `Core.Type{T}`'nin tek örneği `T` nesnesidir.

# Örnekler

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
