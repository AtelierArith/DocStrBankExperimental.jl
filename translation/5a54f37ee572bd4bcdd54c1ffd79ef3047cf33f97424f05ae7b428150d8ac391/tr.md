```
GC.gc([full=true])
```

Çöp toplama işlemi gerçekleştirir. `full` argümanı, toplama türünü belirler: tam bir toplama (varsayılan) tüm canlı nesneleri (yani tam işaretleme) dolaşır ve erişilemeyen tüm nesnelerden bellek geri kazanmalıdır. Artımlı bir toplama yalnızca erişilemeyen genç nesnelerden bellek geri kazanır.

GC, artımlı bir toplama talep edilse bile tam bir toplama gerçekleştirmeye karar verebilir.

!!! uyarı     Aşırı kullanım muhtemelen kötü performansa yol açacaktır.
