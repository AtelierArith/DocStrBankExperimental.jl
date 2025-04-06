```
trylock(lock) -> Başarı (Boolean)
```

Kilidi mevcutsa alır ve başarılıysa `true` döner. Eğer kilit başka bir görev/iş parçacığı tarafından zaten kilitlenmişse, `false` döner.

Her başarılı `trylock`, bir [`unlock`](@ref) ile eşleşmelidir.

`trylock` fonksiyonu, [`islocked`](@ref) ile birleştirildiğinde, *eğer `typeof(lock)` tarafından destekleniyorsa* test-et-test-et-ve-set veya üssel geri çekilme algoritmalarını yazmak için kullanılabilir (belgesini okuyun).
