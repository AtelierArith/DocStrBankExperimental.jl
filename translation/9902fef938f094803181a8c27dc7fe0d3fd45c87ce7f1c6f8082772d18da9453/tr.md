```
permutedims!(dest, src, perm)
```

Dizi `src`'nin boyutlarını permütasyon yaparak `dest` dizisine kaydedin. `perm`, `ndims(src)` uzunluğunda bir permütasyonu belirten bir vektördür. Önceden tahsis edilmiş `dest` dizisinin `size(dest) == size(src)[perm]` olmalı ve tamamen üzerine yazılmalıdır. Yerinde permütasyon desteklenmez ve `src` ile `dest`'in bellek bölgeleri örtüşüyorsa beklenmedik sonuçlar ortaya çıkabilir.

Ayrıca bkz. [`permutedims`](@ref).
