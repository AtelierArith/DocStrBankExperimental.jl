```
Sys.isfreebsd([os])
```

FreeBSD türevi bir işletim sistemi olup olmadığını test etmek için bir predikat. [İşletim Sistemi Varyasyonunu Yönetme](@ref) belgesine bakın.

!!! not
    `Sys.isbsd()` ile karıştırılmamalıdır; bu, FreeBSD'de `true` ancak diğer BSD tabanlı sistemlerde de geçerlidir. `Sys.isfreebsd()` yalnızca FreeBSD'ye atıfta bulunur.


!!! uyumluluk "Julia 1.1"
    Bu fonksiyon en az Julia 1.1 gerektirir.


```
