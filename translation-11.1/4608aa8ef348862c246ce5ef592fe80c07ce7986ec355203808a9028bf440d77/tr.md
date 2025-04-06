```
isempty(collection) -> Bool
```

Bir koleksiyonun boş olup olmadığını belirleyin (hiç elemanı yoksa).

!!! uyarı     `isempty(itr)` bir durum bilgisi olan `itr` yineleyicisinin bir sonraki elemanını tüketebilir, uygun bir [`Base.isdone(itr)`](@ref) yöntemi tanımlanmadıkça. Durum bilgisi olan yineleyiciler *isdone* uygulamalıdır, ancak herhangi bir yineleyici türünü desteklemesi gereken genel kod yazarken `isempty` kullanmaktan kaçınmak isteyebilirsiniz.

# Örnekler

```jldoctest
julia> isempty([])
true

julia> isempty([1 2 3])
false
```
