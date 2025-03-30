```
axes(A)
```

Dizi `A` için geçerli indekslerin demetini döndürür.

Ayrıca bakınız: [`size`](@ref), [`keys`](@ref), [`eachindex`](@ref).

# Örnekler

```jldoctest
julia> A = fill(1, (5,6,7));

julia> axes(A)
(Base.OneTo(5), Base.OneTo(6), Base.OneTo(7))
```
