```
LinearAlgebra.peakflops(n::Integer=4096; eltype::DataType=Float64, ntrials::Integer=3, parallel::Bool=false)
```

`peakflops`, bilgisayarın tepe flop oranını, çift hassasiyet [`gemm!`](@ref LinearAlgebra.BLAS.gemm!) kullanarak hesaplar. Varsayılan olarak, eğer hiçbir argüman belirtilmemişse, `n x n` boyutunda iki `Float64` matrisini çarpar; burada `n = 4096`'dır. Temel BLAS çoklu iş parçacığı kullanıyorsa, daha yüksek flop oranları elde edilir. BLAS iş parçacığı sayısı [`BLAS.set_num_threads(n)`](@ref) ile ayarlanabilir.

Eğer `eltype` anahtar kelime argümanı sağlanırsa, `peakflops`, tepe flop oranını hesaplamak için `eltype` türünde elemanlara sahip matrisler oluşturur.

Varsayılan olarak, `peakflops`, 3 denemeden en iyi zamanlamayı kullanır. Eğer `ntrials` anahtar kelime argümanı sağlanırsa, `peakflops`, en iyi zamanlamayı seçmek için belirtilen kadar deneme yapar.

Eğer `parallel` anahtar kelime argümanı `true` olarak ayarlanırsa, `peakflops`, tüm işçi işlemcilerinde paralel olarak çalıştırılır. Tüm paralel bilgisayarın flop oranı döndürülür. Paralel çalışırken yalnızca 1 BLAS iş parçacığı kullanılır. `n` argümanı, her işlemcide çözülen problemin boyutunu ifade etmeye devam eder.

!!! compat "Julia 1.1"
    Bu fonksiyon en az Julia 1.1 gerektirir. Julia 1.0'da standart kütüphane `InteractiveUtils`'dan mevcuttur.

