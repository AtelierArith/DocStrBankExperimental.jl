```
PartialQuickSort{T <: Union{Integer,OrdinalRange}}
```

Sıralama fonksiyonunun kısmi hızlı sıralama algoritmasını kullanması gerektiğini belirtir. `PartialQuickSort(k)`, `QuickSort` gibi, ancak yalnızca `v` tam olarak sıralandığında `v[k]`'de yer alacak olan elemanları bulup sıralamakla yükümlüdür.

Özellikler:

  * *kararsız*: eşit olan elemanların sıralama düzenini korumaz (örneğin, büyük/küçük harf farkı gözetmeyen bir sıralamada "a" ve "A").
  * *yerinde* bellek içinde.
  * *böl ve fethet*: [`MergeSort`](@ref) ile benzer sıralama stratejisi.

Not edin ki `PartialQuickSort(k)` mutlaka tüm diziyi sıralamak zorunda değildir. Örneğin,

```jldoctest
julia> x = rand(100);

julia> k = 50:100;

julia> s1 = sort(x; alg=QuickSort);

julia> s2 = sort(x; alg=PartialQuickSort(k));

julia> map(issorted, (s1, s2))
(true, false)

julia> map(x->issorted(x[k]), (s1, s2))
(true, true)

julia> s1[k] == s2[k]
true
```
