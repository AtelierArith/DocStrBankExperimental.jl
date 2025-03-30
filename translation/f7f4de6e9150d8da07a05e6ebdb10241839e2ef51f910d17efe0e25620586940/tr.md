```
spmv!(uplo, α, AP, x, β, y)
```

Vektörü `y`'yi `α*A*x + β*y` olarak güncelleyin, burada `A` paket formatında sağlanan simetrik bir matristir `AP`.

`uplo = 'U'` olduğunda, dizi AP, simetrik matrisin üst üçgen kısmını sütun sütun sıralı olarak içermelidir, böylece `AP[1]` `A[1, 1]`'i, `AP[2]` ve `AP[3]` sırasıyla `A[1, 2]` ve `A[2, 2]`'yi içerir ve devam eder.

`uplo = 'L'` olduğunda, dizi AP, simetrik matrisin alt üçgen kısmını sütun sütun sıralı olarak içermelidir, böylece `AP[1]` `A[1, 1]`'i, `AP[2]` ve `AP[3]` sırasıyla `A[2, 1]` ve `A[3, 1]`'yi içerir ve devam eder.

Skalar girişler `α` ve `β` gerçek olmalıdır.

Dizi girişleri `x`, `y` ve `AP` hepsi `Float32` veya `Float64` türünde olmalıdır.

Güncellenmiş `y`'yi döndürün.

!!! compat "Julia 1.5"
    `spmv!` en az Julia 1.5 gerektirir.

