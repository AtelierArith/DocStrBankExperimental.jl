```
spr!(uplo, α, x, AP)
```

Matris `A`'yı `A+α*x*x'` olarak güncelleyin, burada `A` paket formatında sağlanan simetrik bir matristir ve `x` bir vektördür.

`uplo = 'U'` olduğunda, dizi AP, simetrik matrisin üst üçgen kısmını sütun sütun sıralı olarak içermelidir, böylece `AP[1]` `A[1, 1]`'i, `AP[2]` ve `AP[3]` sırasıyla `A[1, 2]` ve `A[2, 2]`'yi içerir ve devam eder.

`uplo = 'L'` olduğunda, dizi AP, simetrik matrisin alt üçgen kısmını sütun sütun sıralı olarak içermelidir, böylece `AP[1]` `A[1, 1]`'i, `AP[2]` ve `AP[3]` sırasıyla `A[2, 1]` ve `A[3, 1]`'i içerir ve devam eder.

Skalar girdi `α` gerçek olmalıdır.

Dizi girdileri `x` ve `AP` tümü `Float32` veya `Float64` türünde olmalıdır. Güncellenmiş `AP`'yi döndürün.

!!! compat "Julia 1.8"
    `spr!` en az Julia 1.8 gerektirir.

