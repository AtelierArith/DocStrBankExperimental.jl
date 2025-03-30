```
memoryref(::GenericMemory, index::Integer)
memoryref(::GenericMemoryRef, index::Integer)
```

Bir bellek nesnesinden ve bir offset indeksinden (1-bazlı) `GenericMemoryRef` oluşturur; bu indeks negatif de olabilir. Bu her zaman bir sınır içindeki nesne döndürür ve bu mümkün değilse (çünkü indeks, temel belleğin dışına kaymaya neden olursa) bir hata fırlatır.
