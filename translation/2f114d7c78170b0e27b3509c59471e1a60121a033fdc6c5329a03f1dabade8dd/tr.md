```
islocked(lock) -> Durum (Boolean)
```

`lock`'ın herhangi bir görev/iş parçacığı tarafından tutulup tutulmadığını kontrol eder. Bu fonksiyon tek başına senkronizasyon için kullanılmamalıdır. Ancak, `islocked` ile [`trylock`](@ref) birleştirildiğinde, test-et-test-et-ve-set veya üssel geri çekilme algoritmalarını yazmak için kullanılabilir *eğer `typeof(lock)` tarafından destekleniyorsa* (belgelerini okuyun).

# Genişletilmiş yardım

Örneğin, `lock` uygulaması aşağıda belgelenen özellikleri karşıladıysa, üssel geri çekilme şu şekilde uygulanabilir.

```julia
nspins = 0
while true
    while islocked(lock)
        GC.safepoint()
        nspins += 1
        nspins > LIMIT && error("timeout")
    end
    trylock(lock) && break
    backoff()
end
```

## Uygulama

Bir kilit uygulamasının `islocked`'ı aşağıdaki özelliklerle tanımlaması ve bunu belgelerinde belirtmesi önerilir.

  * `islocked(lock)` veri yarışı içermemelidir.
  * Eğer `islocked(lock)` `false` dönerse, diğer görevlerden herhangi bir müdahale yoksa `trylock(lock)`'ın hemen çağrılması başarılı olmalıdır ( `true` döner).
