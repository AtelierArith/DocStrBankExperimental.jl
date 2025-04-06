```
unsafe_write(io::IO, ref, nbytes::UInt)
```

`ref`'den `nbytes`'i (bir işaretçiye dönüştürülmüş) `IO` nesnesine kopyalayın.

`T<:IO` alt türlerinin daha verimli uygulamalar sağlamak için aşağıdaki yöntem imzasını geçersiz kılmaları önerilir: `unsafe_write(s::T, p::Ptr{UInt8}, n::UInt)`
