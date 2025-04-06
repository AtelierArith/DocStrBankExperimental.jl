```
map!(function, destination, collection...)
```

[`map`](@ref) gibi, ancak sonucu yeni bir koleksiyona değil `destination`'a kaydeder. `destination`, en küçük koleksiyon kadar büyük olmalıdır.

!!! warning
    Herhangi bir değiştirilmiş argümanın, diğer herhangi bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.


Ayrıca bakınız: [`map`](@ref), [`foreach`](@ref), [`zip`](@ref), [`copyto!`](@ref).

# Örnekler

```jldoctest
julia> a = zeros(3);

julia> map!(x -> x * 2, a, [1, 2, 3]);

julia> a
3-element Vector{Float64}:
 2.0
 4.0
 6.0

julia> map!(+, zeros(Int, 5), 100:999, 1:3)
5-element Vector{Int64}:
 101
 103
 105
   0
   0
```
