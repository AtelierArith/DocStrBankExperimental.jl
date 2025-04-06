```
ReverseOrdering(fwd::Ordering=Forward)
```

Bir sıralamayı tersine çeviren bir sarmalayıcıdır.

Verilen bir `Ordering` `o` için, tüm `a`, `b` için aşağıdakiler geçerlidir:

```
lt(ReverseOrdering(o), a, b) == lt(o, b, a)
```
