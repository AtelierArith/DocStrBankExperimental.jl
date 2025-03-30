```
*(A, B::AbstractMatrix, C)
A * B * C * D
```

3 veya 4 matrisin zincirleme çarpımı, dizilerin boyutlarına dayalı olarak en verimli sırada yapılır. Yani, `(A * B) * C` (3 yoğun matris ile) için gereken skalar çarpım sayısı, `A * (B * C)` için gerekenle karşılaştırılır ve bunlardan hangisinin yürütüleceğine karar verilir.

Son faktör bir vektörse veya ilk faktör transpoze bir vektörse, bunlarla önce ilgilenmek verimlidir. Özellikle `x' * B * y`, sıradan bir sütun-büyük `B::Matrix` için `(x' * B) * y` anlamına gelir. `dot(x, B, y)`'den farklı olarak, bu ara bir dizi ayırır.

İlk veya son faktör bir sayıysa, bu matris çarpımı ile birleştirilecektir ve 5-arg [`mul!`](@ref) kullanılacaktır.

Ayrıca [`muladd`](@ref), [`dot`](@ref) bakınız.

!!! uyumluluk "Julia 1.7"
    Bu optimizasyonlar en az Julia 1.7 gerektirir.

