```
unsafe_read(io::IO, ref, nbytes::UInt)
```

`IO` akış nesnesinden `nbytes`'ı `ref`'e (bir işaretçiye dönüştürülmüş) kopyalar.

`T<:IO` alt türlerinin daha verimli uygulamalar sağlamak için aşağıdaki yöntem imzasını geçersiz kılmaları önerilir: `unsafe_read(s::T, p::Ptr{UInt8}, n::UInt)`
