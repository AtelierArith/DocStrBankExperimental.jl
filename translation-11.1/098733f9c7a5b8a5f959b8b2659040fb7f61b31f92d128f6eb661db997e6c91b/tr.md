```
checkindex(Bool, inds::AbstractUnitRange, index)
```

Verilen `index` değeri `inds` sınırları içinde ise `true` döner. Tüm diziler için indeks olarak davranmak isteyen özel türler, özel bir sınır kontrolü uygulaması sağlamak amacıyla bu yöntemi genişletebilir.

Ayrıca bkz. [`checkbounds`](@ref).

# Örnekler

```jldoctest
julia> checkindex(Bool, 1:20, 8)
true

julia> checkindex(Bool, 1:20, 21)
false
```
