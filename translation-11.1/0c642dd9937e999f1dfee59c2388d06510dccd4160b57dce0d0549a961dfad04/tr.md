```
isopen(object) -> Bool
```

Bir nesnenin - bir akış veya zamanlayıcı gibi - henüz kapatılıp kapatılmadığını belirleyin. Bir nesne kapatıldığında, asla yeni bir olay üretmeyecektir. Ancak, kapatılmış bir akışın hala tamponunda okunacak verileri olabileceğinden, veri okuma yeteneğini kontrol etmek için [`eof`](@ref) kullanın. Bir akışın yazılabilir veya okunabilir olabileceği konusunda bildirim almak için `FileWatching` paketini kullanın.

# Örnekler

```jldoctest
julia> io = open("my_file.txt", "w+");

julia> isopen(io)
true

julia> close(io)

julia> isopen(io)
false
```
