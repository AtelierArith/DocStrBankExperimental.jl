```
-(x)
```

Tekil eksi operatörü.

Ayrıca bakınız: [`abs`](@ref), [`flipsign`](@ref).

# Örnekler

```jldoctest
julia> -1
-1

julia> -(2)
-2

julia> -[1 2; 3 4]
2×2 Matrix{Int64}:
 -1  -2
 -3  -4

julia> -(true)  # Int'e yükseltilir
-1

julia> -(0x003)
0xfffd
```
