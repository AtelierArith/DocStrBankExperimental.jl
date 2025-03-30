```
hpmv!(uplo, α, AP, x, β, y)
```

Vektörü `y`'yi `α*A*x + β*y` olarak güncelleyin, burada `A` paket formatında sağlanan bir Hermit matrisidir `AP`.

`uplo = 'U'` olduğunda, dizi AP, Hermit matrisinin üst üçgen kısmını sütun sütun paketlenmiş olarak içermelidir, böylece `AP[1]` `A[1, 1]`'i, `AP[2]` ve `AP[3]` sırasıyla `A[1, 2]` ve `A[2, 2]`'yi içerir ve devam eder.

`uplo = 'L'` olduğunda, dizi AP, Hermit matrisinin alt üçgen kısmını sütun sütun paketlenmiş olarak içermelidir, böylece `AP[1]` `A[1, 1]`'i, `AP[2]` ve `AP[3]` sırasıyla `A[2, 1]` ve `A[3, 1]`'i içerir ve devam eder.

Skalar girişler `α` ve `β` karmaşık veya reel sayılar olmalıdır.

Dizi girişleri `x`, `y` ve `AP` hepsi `ComplexF32` veya `ComplexF64` türünde olmalıdır.

Güncellenmiş `y`'yi döndürün.

!!! compat "Julia 1.5"
    `hpmv!` en az Julia 1.5 gerektirir.

