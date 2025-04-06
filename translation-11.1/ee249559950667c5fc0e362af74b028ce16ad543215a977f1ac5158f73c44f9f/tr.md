```
reshape(A, dims...) -> AbstractArray
reshape(A, dims) -> AbstractArray
```

`A` ile aynı verilere sahip, ancak farklı boyutlara veya boyut sayısına sahip bir dizi döndürün. İki dizi aynı temel verileri paylaştığı için, sonuç yalnızca `A` değiştirilebilir ise değiştirilebilir ve birinin elemanlarını ayarlamak diğerinin değerlerini değiştirir.

Yeni boyutlar, ya bir argüman listesi olarak ya da bir şekil demeti olarak belirtilebilir. En fazla bir boyut `:` ile belirtilebilir; bu durumda, uzunluğu, belirtilen tüm boyutlarla çarpımının orijinal dizi `A`'nın uzunluğuna eşit olacak şekilde hesaplanır. Toplam eleman sayısı değişmemelidir.

# Örnekler

```jldoctest
julia> A = Vector(1:16)
16-element Vector{Int64}:
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16

julia> reshape(A, (4, 4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> reshape(A, 2, :)
2×8 Matrix{Int64}:
 1  3  5  7   9  11  13  15
 2  4  6  8  10  12  14  16

julia> reshape(1:6, 2, 3)
2×3 reshape(::UnitRange{Int64}, 2, 3) with eltype Int64:
 1  3  5
 2  4  6
```
