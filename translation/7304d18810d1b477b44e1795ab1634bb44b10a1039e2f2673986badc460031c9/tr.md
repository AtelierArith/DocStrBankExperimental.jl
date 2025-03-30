```
Mmap.Anonymous(name::AbstractString="", readonly::Bool=false, create::Bool=true)
```

Dosya ile ilişkilendirilmemiş sıfırlanmış mmapped bellek oluşturmak için bir `IO` benzeri nesne oluşturur, [`mmap`](@ref mmap) içinde kullanılmak üzere. Paylaşılan bellek dizileri oluşturmak için `SharedArray` tarafından kullanılır.

# Örnekler

```jldoctest
julia> using Mmap

julia> anon = Mmap.Anonymous();

julia> isreadable(anon)
true

julia> iswritable(anon)
true

julia> isopen(anon)
true
```
