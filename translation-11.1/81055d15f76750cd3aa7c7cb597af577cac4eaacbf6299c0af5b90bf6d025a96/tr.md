```
init(; n::Integer, delay::Real)
```

`delay` arasında geri izleme (saniye cinsinden ölçülen) ve her bir iş parçacığı başına saklanabilecek `n` talimat işaretçisi sayısını yapılandırın. Her talimat işaretçisi, tek bir kod satırına karşılık gelir; geri izlemeler genellikle uzun bir talimat işaretçisi listesi içerir. Geri izleme başına talimat işaretçileri için 6 boşluk kullanıldığını ve iki NULL son işaretleyicisi saklandığını unutmayın. Mevcut ayarlar, bu işlevi argüman olmadan çağırarak elde edilebilir ve her biri bağımsız olarak anahtar kelimeler kullanılarak veya `(n, delay)` sırasıyla ayarlanabilir.
