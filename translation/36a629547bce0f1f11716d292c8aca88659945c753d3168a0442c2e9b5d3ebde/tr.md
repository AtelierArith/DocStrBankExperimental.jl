```
print([io::IO], xs...)
```

`io`'ya (ve `io` verilmemişse varsayılan çıktı akışına [`stdout`](@ref)) kanonik (süslenmemiş) bir metin temsili yazın. `print` tarafından kullanılan temsil, minimum biçimlendirme içerir ve Julia'ya özgü ayrıntılardan kaçınmaya çalışır.

`print`, `show` çağrısına geri döner, bu nedenle çoğu tür sadece `show` tanımlamalıdır. Eğer türünüzün ayrı bir "düz" temsili varsa `print` tanımlayın. Örneğin, `show` dizeleri tırnak içinde gösterirken, `print` dizeleri tırnaksız gösterir.

Ayrıca bkz. [`println`](@ref), [`string`](@ref), [`printstyled`](@ref).

# Örnekler

```jldoctest
julia> print("Hello World!")
Hello World!
julia> io = IOBuffer();

julia> print(io, "Hello", ' ', :World!)

julia> String(take!(io))
"Hello World!"
```
