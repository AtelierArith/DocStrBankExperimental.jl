```
callers(funcname, [data, lidict], [filename=<filename>], [linerange=<start:stop>]) -> Vector{Tuple{count, lineinfo}}
```

Önceki bir profil çalışmasından, belirli bir fonksiyonu kimin çağırdığını belirleyin. Dosya adını (ve isteğe bağlı olarak, fonksiyonun tanımlandığı satır numaraları aralığını) sağlamak, aşırı yüklenmiş bir yöntemi ayırt etmenizi sağlar. Döndürülen değer, çağrı sayısını ve çağıranın satır bilgilerini içeren bir vektördür. İsteğe bağlı olarak, [`retrieve`](@ref) ile elde edilen geri izleme `data` sağlanabilir; aksi takdirde, mevcut iç profil tamponu kullanılır.
