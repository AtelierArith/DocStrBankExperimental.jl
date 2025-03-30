```
sparse_vcat(A...)
```

Boyut 1 boyunca birleştirir. Bir SparseMatrixCSC nesnesi döner.

!!! uyumluluk "Julia 1.8"
    Bu yöntem Julia 1.8'de eklendi. Daha önceki birleştirme davranışını taklit eder; LinearAlgebra.jl'den özel "sparse" matris türleri ile birleştirme, herhangi bir SparseArray argümanı olmaksızın otomatik olarak seyrek çıktı verir.

