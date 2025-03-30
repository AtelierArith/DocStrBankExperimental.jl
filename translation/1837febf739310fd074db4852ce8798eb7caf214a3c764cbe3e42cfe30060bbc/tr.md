```
*(x, y...)
```

Çarpma operatörü.

İnfix `x*y*z*...` bu fonksiyonu tüm argümanlarla çağırır, yani `*(x, y, z, ...)`, bu da varsayılan olarak `(x*y) * z * ...` şeklinde soldan başlayarak çağrılır.

Yan yana yazım `2pi` gibi ifadeler de `*(2, pi)` çağrısını yapar. Bu işlemin, bir literal `*`'dan daha yüksek önceliğe sahip olduğunu unutmayın. Ayrıca, yan yana yazım "0x..." (x ile başlayan bir değişkenin sıfır katı) yasaktır çünkü bu, işaretsiz tam sayı literal'leriyle çakışır: `0x01 isa UInt8`.

Büyük sayıları çarparken, varsayılan `Int` dahil olmak üzere çoğu tam sayı türü için taşma olasılığının olduğunu unutmayın.

# Örnekler

```jldoctest
julia> 2 * 7 * 8
112

julia> *(2, 7, 8)
112

julia> [2 0; 0 3] * [1, 10]  # matris * vektör
2-element Vector{Int64}:
  2
 30

julia> 1/2pi, 1/2*pi  # yan yana yazım daha yüksek önceliğe sahiptir
(0.15915494309189535, 1.5707963267948966)

julia> x = [1, 2]; x'x  # adjoint vektör * vektör
5
```
