```
bir şey(x...)
```

Argümanlar arasında [`nothing`](@ref) ile eşit olmayan ilk değeri döndürün, eğer varsa. Aksi takdirde bir hata fırlatın. [`Some`](@ref) türündeki argümanlar açılır.

Ayrıca bkz. [`coalesce`](@ref), [`skipmissing`](@ref), [`@something`](@ref).

# Örnekler

```jldoctest
julia> bir şey(nothing, 1)
1

julia> bir şey(Some(1), nothing)
1

julia> bir şey(Some(nothing), 2) === nothing
true

julia> bir şey(missing, nothing)
missing

julia> bir şey(nothing, nothing)
HATA: ArgumentError: Değer argümanı yok
```
