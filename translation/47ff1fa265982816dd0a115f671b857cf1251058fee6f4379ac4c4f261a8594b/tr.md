```
digits!(dizi, n::Tam sayı; taban::Tam sayı = 10)
```

Verilen tabanda `n`'nin basamaklarını içeren bir dizi doldurur. Daha anlamlı basamaklar daha yüksek indekslerde bulunur. Eğer dizi uzunluğu yetersizse, en az anlamlı basamaklar dizi uzunluğuna kadar doldurulur. Eğer dizi uzunluğu fazla ise, fazlalık kısmı sıfırlarla doldurulur.

# Örnekler

```jldoctest
julia> digits!([2, 2, 2, 2], 10, base = 2)
4-element Vector{Int64}:
 0
 1
 0
 1

julia> digits!([2, 2, 2, 2, 2, 2], 10, base = 2)
6-element Vector{Int64}:
 0
 1
 0
 1
 0
 0
```
