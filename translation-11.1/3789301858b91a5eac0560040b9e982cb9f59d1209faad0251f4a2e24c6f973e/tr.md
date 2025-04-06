```
skipmissing(itr)
```

`itr` içindeki [`missing`](@ref) değerlerini atlayarak elemanlar üzerinde bir iteratör döndürür. Döndürülen nesne, `itr` indekslenebilir ise `itr`'nin indeksleri kullanılarak indekslenebilir. Eksik değerlere karşılık gelen indeksler geçerli değildir: bunlar [`keys`](@ref) ve [`eachindex`](@ref) tarafından atlanır ve bunları kullanmaya çalıştığınızda bir `MissingException` hatası fırlatılır.

`itr` içindeki eksik olmayan değerleri içeren bir `Array` elde etmek için [`collect`](@ref) kullanın. `itr` çok boyutlu bir dizi olsa bile, sonuç her zaman bir `Vector` olacaktır çünkü eksikleri kaldırırken girişin boyutlarını korumak mümkün değildir.

Ayrıca [`coalesce`](@ref), [`ismissing`](@ref), [`something`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> x = skipmissing([1, missing, 2])
skipmissing(Union{Missing, Int64}[1, missing, 2])

julia> sum(x)
3

julia> x[1]
1

julia> x[2]
HATA: MissingException: indeks (2,) üzerindeki değer eksik
[...]

julia> argmax(x)
3

julia> collect(keys(x))
2-element Vector{Int64}:
 1
 3

julia> collect(skipmissing([1, missing, 2]))
2-element Vector{Int64}:
 1
 2

julia> collect(skipmissing([1 missing; 2 missing]))
2-element Vector{Int64}:
 1
 2
```
