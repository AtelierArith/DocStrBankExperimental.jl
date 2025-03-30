```
Sys.isbsd([os])
```

BSD türevi bir işletim sistemi olup olmadığını test etmek için bir predikattır. [İşletim Sistemi Varyasyonunu Yönetme](@ref) belgesine bakın.

!!! not
    Darwin çekirdeği BSD'den türemiştir, bu da `Sys.isbsd()`'nin macOS sistemlerinde `true` olduğu anlamına gelir. Bir predikattan macOS'u hariç tutmak için `Sys.isbsd() && !Sys.isapple()` kullanın.

