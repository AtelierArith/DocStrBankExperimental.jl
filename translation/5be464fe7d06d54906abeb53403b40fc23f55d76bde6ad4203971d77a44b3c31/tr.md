```
sparse_hvcat(rows::Tuple{Vararg{Int}}, values...)
```

Sıkıştırılmış yatay ve dikey birleştirme tek bir çağrıda. Bu fonksiyon blok matris sözdizimi için çağrılır. İlk argüman, her blok satırında birleştirilecek argüman sayısını belirtir.

!!! compat "Julia 1.8"
    Bu yöntem Julia 1.8'de eklendi. Daha önceki birleştirme davranışını taklit eder; burada LinearAlgebra.jl'den özel "sparse" matris türleri ile birleştirme, herhangi bir SparseArray argümanı olmaksızın otomatik olarak sıkıştırılmış çıktı verir.

