```
empty(v::AbstractVector, [eltype])
```

Boş bir vektör oluşturur, `v`'ye benzer, isteğe bağlı olarak `eltype`'i değiştirir.

Ayrıca bakınız: [`empty!`](@ref), [`isempty`](@ref), [`isassigned`](@ref).

# Örnekler

```jldoctest
julia> empty([1.0, 2.0, 3.0])
Float64[]

julia> empty([1.0, 2.0, 3.0], String)
String[]
```
