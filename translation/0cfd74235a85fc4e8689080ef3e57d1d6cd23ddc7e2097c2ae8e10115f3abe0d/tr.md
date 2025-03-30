```
fetch(;include_meta = true) -> data
```

Profilin geri izleme tamponunun bir kopyasını döndürür. `data` içindeki değerlerin yalnızca bu makinede ve mevcut oturumda anlamı olduğunu unutmayın, çünkü bu, JIT derlemesinde kullanılan tam bellek adreslerine bağlıdır. Bu işlev esasen dahili kullanım içindir; çoğu kullanıcı için [`retrieve`](@ref) daha iyi bir seçim olabilir. Varsayılan olarak, threadid ve taskid gibi meta veriler dahildir. Meta verileri kaldırmak için `include_meta`'yı `false` olarak ayarlayın.
