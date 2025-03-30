```
unique(itr)
```

Koleksiyon `itr`'nin yalnızca benzersiz elemanlarını içeren bir dizi döndürür; bu elemanlar [`isequal`](@ref) ve [`hash`](@ref) tarafından belirlenir ve her bir eşdeğer eleman setinin ilk ortaya çıktığı sıraya göre sıralanır. Girişin eleman türü korunur.

Ayrıca bkz: [`unique!`](@ref), [`allunique`](@ref), [`allequal`](@ref).

# Örnekler

```jldoctest
julia> unique([1, 2, 6, 2])
3-element Vector{Int64}:
 1
 2
 6

julia> unique(Real[1, 1.0, 2])
2-element Vector{Real}:
 1
 2
```
