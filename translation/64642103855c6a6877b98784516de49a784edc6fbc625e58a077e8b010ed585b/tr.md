```
checkbounds(Bool, A, I...)
```

Belirtilen indekslerin `I`, verilen dizi `A` için sınırlar içinde olup olmadığını kontrol etmek için `true` döner. `AbstractArray`'ın alt türleri, özel sınır kontrolü davranışları sağlamaları gerekiyorsa bu yöntemi özelleştirmelidir; ancak birçok durumda `A`'nın indekslerine ve [`checkindex`](@ref) yöntemine güvenilebilir.

Ayrıca bkz. [`checkindex`](@ref).

# Örnekler

```jldoctest
julia> A = rand(3, 3);

julia> checkbounds(Bool, A, 2)
true

julia> checkbounds(Bool, A, 3, 4)
false

julia> checkbounds(Bool, A, 1:3)
true

julia> checkbounds(Bool, A, 1:3, 2:4)
false
```
