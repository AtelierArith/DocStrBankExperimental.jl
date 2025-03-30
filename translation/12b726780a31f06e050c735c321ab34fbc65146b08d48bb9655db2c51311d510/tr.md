```
indexpids(S::SharedArray)
```

Şu anki işçi işleminin `SharedArray`'ı eşleyen işçi listesindeki indeksini döndürür (yani `procs(S)` tarafından döndürülen aynı listede), veya `SharedArray` yerel olarak eşlenmemişse 0 döner.
