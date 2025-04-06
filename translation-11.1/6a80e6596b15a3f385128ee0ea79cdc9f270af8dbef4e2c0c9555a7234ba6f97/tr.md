```
Condition()
```

Görevlerin bekleyebileceği bir kenar tetiklemeli olay kaynağı oluşturur. `Condition` üzerinde [`wait`](@ref) çağrısı yapan görevler askıya alınır ve sıraya alınır. Daha sonra `Condition` üzerinde [`notify`](@ref) çağrısı yapıldığında görevler uyandırılır. Bir koşulda beklemek, bir değer döndürebilir veya [`notify`](@ref) 'nin isteğe bağlı argümanları kullanıldığında bir hata oluşturabilir. Kenar tetikleme, yalnızca [`notify`](@ref) çağrıldığında bekleyen görevlerin uyandırılabileceği anlamına gelir. Seviye tetiklemeli bildirimler için, bir bildirimin olup olmadığını takip etmek için ekstra bir durum tutmalısınız. [`Channel`](@ref) ve [`Threads.Event`](@ref) türleri bunu yapar ve seviye tetiklemeli olaylar için kullanılabilir.

Bu nesne THREAD-GÜVENLİ değildir. Thread-güvenli bir versiyon için [`Threads.Condition`](@ref) 'e bakın.
