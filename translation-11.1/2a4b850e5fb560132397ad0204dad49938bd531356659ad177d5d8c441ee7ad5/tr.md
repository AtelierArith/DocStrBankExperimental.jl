```
StepRangeLen(         ref::R, step::S, len, [offset=1]) where {  R,S}
StepRangeLen{T,R,S}(  ref::R, step::S, len, [offset=1]) where {T,R,S}
StepRangeLen{T,R,S,L}(ref::R, step::S, len, [offset=1]) where {T,R,S,L}
```

Bir aralık `r` burada `r[i]` değerleri `T` türünde üretir (ilk formda, `T` otomatik olarak çıkarılır), bir `ref`erans değeri, bir `step` ve `len`gth ile parametrelenmiştir. Varsayılan olarak `ref`, başlangıç değeri `r[1]`dir, ancak alternatif olarak bunu `r[offset]` değerinin değeri olarak sağlayabilirsiniz, burada başka bir indeks için `1 <= offset <= len`. `a:b` veya `a:b:c` sözdizimi, `a`, `b` veya `c`'nin herhangi birinin ondalık sayılar olduğu durumlarda bir `StepRangeLen` oluşturur.

!!! compat "Julia 1.7"
    4. tür parametresi `L`, en az Julia 1.7'yi gerektirir.

