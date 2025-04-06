```
println([io::IO], xs...)
```

`xs`'yi `io`'ya yazdırır ( [`print`](@ref) kullanarak) ve ardından bir yeni satır ekler. Eğer `io` sağlanmamışsa, varsayılan çıkış akışına [`stdout`](@ref) yazdırır.

Renkler eklemek için [`printstyled`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> println("Merhaba, dünya")
Merhaba, dünya

julia> io = IOBuffer();

julia> println(io, "Merhaba", ',', " dünya.")

julia> String(take!(io))
"Merhaba, dünya.\n"
```
