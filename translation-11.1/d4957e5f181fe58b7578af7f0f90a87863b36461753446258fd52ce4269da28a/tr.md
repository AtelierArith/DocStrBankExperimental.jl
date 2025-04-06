```
circcopy!(dest, src)
```

`src`'yi `dest`'ye kopyalar, her boyutu uzunluğuna göre modül alarak indeksler. `src` ve `dest` aynı boyutta olmalıdır, ancak indekslerinde kaydırma olabilir; herhangi bir kaydırma (dairesel) sarılmaya neden olur. Eğer diziler örtüşen indekslere sahipse, o örtüşme alanında `dest`, `src` ile aynı olur.

!!! warning
    Herhangi bir değiştirilmiş argümanın başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.


Ayrıca bkz: [`circshift`](@ref).

# Örnekler

```julia-repl
julia> src = reshape(Vector(1:16), (4,4))
4×4 Array{Int64,2}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> dest = OffsetArray{Int}(undef, (0:3,2:5))

julia> circcopy!(dest, src)
OffsetArrays.OffsetArray{Int64,2,Array{Int64,2}} with indices 0:3×2:5:
 8  12  16  4
 5   9  13  1
 6  10  14  2
 7  11  15  3

julia> dest[1:3,2:4] == src[1:3,2:4]
true
```
