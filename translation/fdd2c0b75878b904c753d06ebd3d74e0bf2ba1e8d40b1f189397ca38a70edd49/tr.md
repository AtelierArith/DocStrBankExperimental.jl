```
request(m::AbstractMenu; cursor=1)
```

Menüyü görüntüler ve etkileşimli moda girer. `cursor`, başlangıç imleç konumu için kullanılan öğe numarasını belirtir. `cursor`, ya bir `Int` ya da bir `RefValue{Int}` olabilir. İkincisi, imleç konumunun dışarıdan gözlemlenmesi ve kontrolü için yararlıdır.

`selected(m)` döner.

!!! compat "Julia 1.6"
    `cursor` argümanı Julia 1.6 veya daha yenisini gerektirir.

