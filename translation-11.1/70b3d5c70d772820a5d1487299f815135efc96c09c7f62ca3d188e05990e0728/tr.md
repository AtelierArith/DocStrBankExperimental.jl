```
Sys.isnetbsd([os])
```

NetBSD türevi bir işletim sistemi olup olmadığını test etmek için bir predikattır. [İşletim Sistemi Varyasyonunu Yönetme](@ref) belgesine bakın.

!!! not
    `Sys.isbsd()` ile karıştırılmamalıdır; bu, NetBSD'de `true` ancak diğer BSD tabanlı sistemlerde de geçerlidir. `Sys.isnetbsd()` yalnızca NetBSD'yi ifade eder.


!!! uyumluluk "Julia 1.1"
    Bu fonksiyon en az Julia 1.1 gerektirir.

