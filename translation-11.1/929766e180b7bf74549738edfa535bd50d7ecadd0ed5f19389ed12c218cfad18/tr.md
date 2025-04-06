```
copyto!(dest::AbstractArray, src) -> dest
```

Tüm elemanları `src` koleksiyonundan `dest` dizisine kopyalar; `dest`'in uzunluğu `src`'nin uzunluğu `n`'den büyük veya eşit olmalıdır. `dest`'in ilk `n` elemanı üzerine yazılır, diğer elemanlar dokunulmadan bırakılır.

Ayrıca bkz. [`copy!`](@ref Base.copy!), [`copy`](@ref).

!!! uyarı     Herhangi bir değiştirilmiş argümanın, başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.

# Örnekler

```jldoctest
julia> x = [1., 0., 3., 0., 5.];

julia> y = zeros(7);

julia> copyto!(y, x);

julia> y
7-element Vector{Float64}:
 1.0
 0.0
 3.0
 0.0
 5.0
 0.0
 0.0
```
