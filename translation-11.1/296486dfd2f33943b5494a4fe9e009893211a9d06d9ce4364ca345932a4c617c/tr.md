```
LinearIndices(A::AbstractArray)
```

`A` ile aynı şekle ve [`axes`](@ref) sahip bir `LinearIndices` dizisi döndürür, `A`'daki her bir girişin lineer indeksini tutar. Bu diziyi kartezyen indekslerle indekslemek, bunları lineer indekslere eşleştirmeyi sağlar.

Geleneksel indeksleme ile diziler (indeksler 1'den başlar) veya herhangi bir çok boyutlu dizi için, lineer indeksler 1'den `length(A)`'ye kadar uzanır. Ancak, `AbstractVector`'lar için lineer indeksler `axes(A, 1)`'dir ve bu nedenle alışılmadık indekslemeye sahip vektörler için 1'den başlamaz.

Bu fonksiyonu çağırmak, lineer indekslemeyi kullanan algoritmalar yazmanın "güvenli" yoludur.

# Örnekler

```jldoctest
julia> A = fill(1, (5,6,7));

julia> b = LinearIndices(A);

julia> extrema(b)
(1, 210)
```

```
LinearIndices(inds::CartesianIndices) -> R
LinearIndices(sz::Dims) -> R
LinearIndices((istart:istop, jstart:jstop, ...)) -> R
```

Belirtilen şekle veya [`axes`](@ref) ile aynı olan bir `LinearIndices` dizisi döndürür.

# Örnekler

Bu yapıcının ana amacı, kartezyen indekslemeden lineer indekslemeye sezgisel bir dönüşümdür:

```jldoctest
julia> linear = LinearIndices((1:3, 1:2))
3×2 LinearIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}}:
 1  4
 2  5
 3  6

julia> linear[1,2]
4
```
