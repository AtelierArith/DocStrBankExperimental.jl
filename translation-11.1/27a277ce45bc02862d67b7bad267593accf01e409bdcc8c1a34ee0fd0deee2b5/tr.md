```
splitpath(path::AbstractString) -> Vector{String}
```

Bir dosya yolunu tüm yol bileşenlerine ayırır. Bu, `joinpath`'in tersidir. Yolda bulunan her dizin veya dosya için bir alt dize içeren bir dizi döner, kök dizin mevcutsa onu da içerir.

!!! compat "Julia 1.1"
    Bu fonksiyon en az Julia 1.1 gerektirir.


# Örnekler

```jldoctest
julia> splitpath("/home/myuser/example.jl")
4-element Vector{String}:
 "/"
 "home"
 "myuser"
 "example.jl"
```
