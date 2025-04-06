```
Profile.Allocs.print([io::IO = stdout,] [data::AllocResults = fetch()]; kwargs...)
```

Profiling sonuçlarını `io`'ya (varsayılan olarak, `stdout`) yazdırır. Eğer bir `data` vektörü sağlamazsanız, birikmiş geri izlerin içsel tamponu kullanılacaktır.

Geçerli anahtar kelime argümanlarının açıklaması için `Profile.print`'e bakın.
