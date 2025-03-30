```
sign(x)
```

`x==0` ise sıfır döndür ve aksi takdirde $x/|x|$ (yani, reel `x` için ±1) döndür.

Ayrıca bkz. [`signbit`](@ref), [`zero`](@ref), [`copysign`](@ref), [`flipsign`](@ref).

# Örnekler

```jldoctest
julia> sign(-4.0)
-1.0

julia> sign(99)
1

julia> sign(-0.0)
-0.0

julia> sign(0 + im)
0.0 + 1.0im
```
