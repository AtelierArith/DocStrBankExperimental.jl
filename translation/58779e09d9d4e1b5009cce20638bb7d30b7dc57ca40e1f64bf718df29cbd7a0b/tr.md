```
in(item, collection) -> Bool
∈(item, collection) -> Bool
```

Bir öğenin verilen koleksiyonda olup olmadığını belirleyin; bu, öğenin koleksiyonu iterasyona tabi tutarak üretilen değerlerden biriyle [`==`](@ref) eşit olduğu anlamına gelir. Bir `Bool` değeri döndürün, ancak `item` [`missing`](@ref) ise veya `collection` `item` hariç `missing` içeriyorsa, bu durumda `missing` döndürülür ([üç değerli mantık](https://en.wikipedia.org/wiki/Three-valued_logic), [`any`](@ref) ve [`==`](@ref) işlevinin davranışını yansıtır).

Bazı koleksiyonlar biraz farklı bir tanıma sahiptir. Örneğin, [`Set`](@ref)ler öğenin elemanlardan biriyle [`isequal`](@ref) olup olmadığını kontrol eder; [`Dict`](@ref)ler `key=>value` çiftlerini arar ve `key` [`isequal`](@ref) kullanılarak karşılaştırılır.

Bir sözlükte bir anahtarın varlığını test etmek için [`haskey`](@ref) veya `k in keys(dict)` kullanın. Yukarıda bahsedilen koleksiyonlar için sonuç her zaman bir `Bool`'dur.

`in.(items, collection)` veya `items .∈ collection` ile yayılma (broadcasting) yaparken, hem `item` hem de `collection` üzerinde yayılma yapılır; bu genellikle istenen bir durum değildir. Örneğin, her iki argüman da vektörse (ve boyutlar eşleşiyorsa), sonuç, `items` koleksiyonundaki her değerin `collection`'daki karşılık gelen pozisyondaki değerde `in` olup olmadığını belirten bir vektördür. `items`'deki her değerin `collection`'da olup olmadığını belirten bir vektör almak için `collection`'ı bir demet (tuple) veya `Ref` içine sarın; şöyle: `in.(items, Ref(collection))` veya `items .∈ Ref(collection)`.

Ayrıca bakınız: [`∉`](@ref), [`insorted`](@ref), [`contains`](@ref), [`occursin`](@ref), [`issubset`](@ref).

# Örnekler

```jldoctest
julia> a = 1:3:20
1:3:19

julia> 4 in a
true

julia> 5 in a
false

julia> missing in [1, 2]
missing

julia> 1 in [2, missing]
missing

julia> 1 in [1, missing]
true

julia> missing in Set([1, 2])
false

julia> (1=>missing) in Dict(1=>10, 2=>20)
missing

julia> [1, 2] .∈ [2, 3]
2-element BitVector:
 0
 0

julia> [1, 2] .∈ ([2, 3],)
2-element BitVector:
 0
 1
```
