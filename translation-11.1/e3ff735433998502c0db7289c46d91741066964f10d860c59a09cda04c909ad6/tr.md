```
hvncat(dim::Int, row_first, values...)
hvncat(dims::Tuple{Vararg{Int}}, row_first, values...)
hvncat(shape::Tuple{Vararg{Tuple}}, row_first, values...)
```

Birçok `values`'ı tek bir çağrıda yatay, dikey ve n-boyutlu birleştirme.

Bu fonksiyon blok matris sözdizimi için çağrılır. İlk argüman, bir tuple olarak birleştirmenin şeklinin belirlenmesini sağlar veya her eksen boyunca anahtar sayıdaki elemanları belirten boyutları belirtir ve çıktı boyutlarını belirlemek için kullanılır. `dims` biçimi daha performanslıdır ve birleştirme işlemi her eksen boyunca aynı sayıda eleman olduğunda varsayılan olarak kullanılır (örneğin, [a b; c d;;; e f ; g h]). `shape` biçimi, her eksen boyunca eleman sayısının dengesiz olduğu durumlarda kullanılır (örneğin, [a b ; c]). Dengesiz sözdizimi ek doğrulama yükü gerektirir. `dim` biçimi yalnızca bir boyut boyunca birleştirme için bir optimizasyondur. `row_first`, `values`'ın nasıl sıralandığını belirtir. `shape`'ın birinci ve ikinci elemanlarının anlamı da `row_first`'a göre değiştirilir.

# Örnekler

```jldoctest
julia> a, b, c, d, e, f = 1, 2, 3, 4, 5, 6
(1, 2, 3, 4, 5, 6)

julia> [a b c;;; d e f]
1×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  2  3

[:, :, 2] =
 4  5  6

julia> hvncat((2,1,3), false, a,b,c,d,e,f)
2×1×3 Array{Int64, 3}:
[:, :, 1] =
 1
 2

[:, :, 2] =
 3
 4

[:, :, 3] =
 5
 6

julia> [a b;;; c d;;; e f]
1×2×3 Array{Int64, 3}:
[:, :, 1] =
 1  2

[:, :, 2] =
 3  4

[:, :, 3] =
 5  6

julia> hvncat(((3, 3), (3, 3), (6,)), true, a, b, c, d, e, f)
1×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  2  3

[:, :, 2] =
 4  5  6
```

# Argümanların oluşturulması için örnekler

```
[a b c ; d e f ;;;
 g h i ; j k l ;;;
 m n o ; p q r ;;;
 s t u ; v w x]
⇒ dims = (2, 3, 4)

[a b ; c ;;; d ;;;;]
 ___   _     _
 2     1     1 = her satırdaki elemanlar (2, 1, 1)
 _______     _
 3           1 = her sütundaki elemanlar (3, 1)
 _____________
 4             = her 3d dilimdeki elemanlar (4,)
 _____________
 4             = her 4d dilimdeki elemanlar (4,)
⇒ shape = ((2, 1, 1), (3, 1), (4,), (4,)) ile `row_first` = true
```
