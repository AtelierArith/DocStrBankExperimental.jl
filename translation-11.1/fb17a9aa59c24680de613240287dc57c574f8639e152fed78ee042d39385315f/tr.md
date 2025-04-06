```
∉(öğe, koleksiyon) -> Bool
∌(koleksiyon, öğe) -> Bool
```

`∈` ve `∋`'nin olumsuzlaması, yani `öğe`nin `koleksiyon`da olmadığını kontrol eder.

`items .∉ koleksiyon` ile yayılma (broadcasting) yapıldığında, hem `öğe` hem de `koleksiyon` yayılır, bu genellikle istenen bir durum değildir. Örneğin, her iki argüman da vektörse (ve boyutlar eşleşiyorsa), sonuç, `items` koleksiyonundaki her değerin `koleksiyon`daki karşılık gelen pozisyondaki değerde olmadığını belirten bir vektördür. `items`'in `koleksiyon`da olmadığını belirten bir vektör almak için, `koleksiyon`u bir demet (tuple) veya `Ref` içine sarın, şöyle: `items .∉ Ref(koleksiyon)`.

# Örnekler

```jldoctest
julia> 1 ∉ 2:4
true

julia> 1 ∉ 1:3
false

julia> [1, 2] .∉ [2, 3]
2-element BitVector:
 1
 1

julia> [1, 2] .∉ ([2, 3],)
2-element BitVector:
 1
 0
```
