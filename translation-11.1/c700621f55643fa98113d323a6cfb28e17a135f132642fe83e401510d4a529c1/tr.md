```
ExponentialBackOff(; n=1, first_delay=0.05, max_delay=10.0, factor=5.0, jitter=0.1)
```

Bir [`Float64`](@ref) iteratörü, `n` uzunluğunda ve elemanları `factor` * (1 ± `jitter`) aralığında üssel olarak artar. İlk eleman `first_delay`'dir ve tüm elemanlar `max_delay`'e sıkıştırılmıştır.
