```
last(coll)
```

Sıralı bir koleksiyonun son elemanını alır, eğer O(1) zamanında hesaplanabiliyorsa. Bu, son indeksi almak için [`lastindex`](@ref) çağrılarak gerçekleştirilir. Boş olsa bile bir [`AbstractRange`](@ref) son noktasını döndürür.

Ayrıca [`first`](@ref), [`endswith`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> last(1:2:10)
9

julia> last([1; 2; 3; 4])
4
```
