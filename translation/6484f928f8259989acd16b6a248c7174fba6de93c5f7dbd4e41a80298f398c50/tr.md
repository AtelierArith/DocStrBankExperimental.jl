```
sizeof(T::DataType)
sizeof(obj)
```

Verilen `DataType` `T`'nin, varsa, kanonik ikili temsilinin boyutu, bayt cinsinden. Veya `DataType` olmayan `obj` nesnesinin boyutu, bayt cinsinden.

Ayrıca [`Base.summarysize`](@ref) bakınız.

# Örnekler

```jldoctest
julia> sizeof(Float32)
4

julia> sizeof(ComplexF64)
16

julia> sizeof(1.0)
8

julia> sizeof(collect(1.0:10.0))
80

julia> struct StructWithPadding
           x::Int64
           flag::Bool
       end

julia> sizeof(StructWithPadding) # padding nedeniyle alanların `sizeof` toplamı değil
16

julia> sizeof(Int64) + sizeof(Bool) # yukarıdakinden farklı
9
```

Eğer `DataType` `T`'nin belirli bir boyutu yoksa, bir hata fırlatılır.

```jldoctest
julia> sizeof(AbstractArray)
HATA: Soyut tür AbstractArray'ın kesin bir boyutu yoktur.
Yığın izi:
[...]
```
