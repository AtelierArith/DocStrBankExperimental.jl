```
sortslices(A; dims, alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Bir dizi `A`'nın dilimlerini sıralar. Gerekli anahtar kelime argümanı `dims` ya bir tamsayı ya da tamsayılar demeti olmalıdır. Sıralamanın yapıldığı boyut(lar)ı belirtir.

Örneğin, eğer `A` bir matris ise, `dims=1` satırları sıralar, `dims=2` sütunları sıralar. Tek boyutlu dilimlerde varsayılan karşılaştırma fonksiyonu sıralamayı leksikografik olarak yapar.

Kalan anahtar kelime argümanları için [`sort!`](@ref) belgesine bakın.

# Örnekler

```jldoctest
julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1) # Satırları sırala
3×3 Matrix{Int64}:
 -1   6  4
  7   3  5
  9  -2  8

julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1, lt=(x,y)->isless(x[2],y[2]))
3×3 Matrix{Int64}:
  9  -2  8
  7   3  5
 -1   6  4

julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1, rev=true)
3×3 Matrix{Int64}:
  9  -2  8
  7   3  5
 -1   6  4

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2) # Sütunları sırala
3×3 Matrix{Int64}:
  3   5  7
 -1  -4  6
 -2   8  9

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2, alg=InsertionSort, lt=(x,y)->isless(x[2],y[2]))
3×3 Matrix{Int64}:
  5   3  7
 -4  -1  6
  8  -2  9

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2, rev=true)
3×3 Matrix{Int64}:
 7   5   3
 6  -4  -1
 9   8  -2
```

# Daha yüksek boyutlar

`sortslices`, daha yüksek boyutlara doğal olarak genişler. Örneğin, eğer `A` 2x2x2 bir dizi ise, `sortslices(A, dims=3)` 3. boyuttaki dilimleri sıralar ve 2x2 dilimleri `A[:, :, 1]` ve `A[:, :, 2]` karşılaştırma fonksiyonuna geçirir. Daha yüksek boyutlu dilimlerde varsayılan bir sıralama olmadığını unutmayın, ancak böyle bir sıralamayı belirtmek için `by` veya `lt` anahtar kelime argümanını kullanabilirsiniz.

Eğer `dims` bir demet ise, `dims` içindeki boyutların sırası önemlidir ve dilimlerin lineer sırasını belirtir. Örneğin, eğer `A` üç boyutlu ise ve `dims` `(1, 2)` ise, ilk iki boyutun sıralamaları yeniden düzenlenir, böylece (kalan üçüncü boyutun) dilimleri sıralanır. Eğer `dims` `(2, 1)` olursa, aynı dilimler alınır, ancak sonuç sırası satır-büyük olur.

# Daha yüksek boyutlu örnekler

```
julia> A = [4 3; 2 1 ;;; 'A' 'B'; 'C' 'D']
2×2×2 Array{Any, 3}:
[:, :, 1] =
 4  3
 2  1

[:, :, 2] =
 'A'  'B'
 'C'  'D'

julia> sortslices(A, dims=(1,2))
2×2×2 Array{Any, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 'D'  'B'
 'C'  'A'

julia> sortslices(A, dims=(2,1))
2×2×2 Array{Any, 3}:
[:, :, 1] =
 1  2
 3  4

[:, :, 2] =
 'D'  'C'
 'B'  'A'

julia> sortslices(reshape([5; 4; 3; 2; 1], (1,1,5)), dims=3, by=x->x[1,1])
1×1×5 Array{Int64, 3}:
[:, :, 1] =
 1

[:, :, 2] =
 2

[:, :, 3] =
 3

[:, :, 4] =
 4

[:, :, 5] =
 5
```
