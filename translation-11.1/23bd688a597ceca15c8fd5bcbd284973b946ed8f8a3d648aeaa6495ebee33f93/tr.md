```
isconcretetype(T)
```

`T` türünün somut bir tür olup olmadığını belirleyin, yani doğrudan örnekleri (değerler `x` böyle ki `typeof(x) === T`) olabilir. `isabstracttype(T)`'nin olumsuzlaması olmadığını unutmayın. Eğer `T` bir tür değilse, `false` döndürün.

Ayrıca bakınız: [`isbits`](@ref), [`isabstracttype`](@ref), [`issingletontype`](@ref).

# Örnekler

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
