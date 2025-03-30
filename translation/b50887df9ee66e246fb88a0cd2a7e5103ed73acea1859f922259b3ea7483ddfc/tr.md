```
findlast(A)
```

`A` içindeki son `true` değerinin indeksini veya anahtarını döndürür. `A` içinde `true` değeri yoksa `nothing` döner.

İndeksler veya anahtarlar, [`keys(A)`](@ref) ve [`pairs(A)`](@ref) tarafından döndürülenlerle aynı türdedir.

Ayrıca bakınız: [`findfirst`](@ref), [`findprev`](@ref), [`findall`](@ref).

# Örnekler

```jldoctest
julia> A = [true, false, true, false]
4-element Vector{Bool}:
 1
 0
 1
 0

julia> findlast(A)
3

julia> A = falses(2,2);

julia> findlast(A) # hiçbir şey döndürmez, ancak REPL'de yazdırılmaz

julia> A = [true false; true false]
2×2 Matrix{Bool}:
 1  0
 1  0

julia> findlast(A)
CartesianIndex(2, 1)
```
