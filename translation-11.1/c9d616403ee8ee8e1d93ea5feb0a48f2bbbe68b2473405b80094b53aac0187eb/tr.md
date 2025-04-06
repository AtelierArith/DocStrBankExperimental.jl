```
fetch(x::Future)
```

Bir [`Future`](@ref) değerini bekleyin ve alın. Alınan değer yerel olarak önbelleğe alınır. Aynı referans üzerindeki `fetch` çağrıları önbelleğe alınan değeri döndürür. Uzak değer bir istisna ise, uzak istisnayı ve geri izlemeyi yakalayan bir [`RemoteException`](@ref) fırlatır.
