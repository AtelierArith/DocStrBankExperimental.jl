```
findfirst(A)
```

`A` içindeki ilk `true` değerinin indeksini veya anahtarını döndürür. Böyle bir değer bulunamazsa `nothing` döner. Diğer türdeki değerleri aramak için, ilk argüman olarak bir predikat geçirin.

İndeksler veya anahtarlar, [`keys(A)`](@ref) ve [`pairs(A)`](@ref) tarafından döndürülenlerle aynı türdedir.

Ayrıca bakınız: [`findall`](@ref), [`findnext`](@ref), [`findlast`](@ref), [`searchsortedfirst`](@ref).

# Örnekler

```jldoctest
julia> A = [false, false, true, false]
4-element Vector{Bool}:
 0
 0
 1
 0

julia> findfirst(A)
3

julia> findfirst(falses(3)) # hiçbir şey döner, ancak REPL'de yazdırılmaz

julia> A = [false false; true false]
2×2 Matrix{Bool}:
 0  0
 1  0

julia> findfirst(A)
CartesianIndex(2, 1)
```
