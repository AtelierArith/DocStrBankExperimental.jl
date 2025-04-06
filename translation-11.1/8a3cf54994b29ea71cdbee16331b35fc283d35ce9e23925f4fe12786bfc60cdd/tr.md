```
@showtime expr
```

`@time` gibi, ancak referans için değerlendirilen ifadeyi de yazdırır.

!!! uyum "Julia 1.8"
    Bu makro Julia 1.8'de eklendi.


Ayrıca bkz. [`@time`](@ref).

```julia-repl
julia> @showtime sleep(1)
sleep(1): 1.002164 saniye (4 tahsis: 128 bayt)
```
