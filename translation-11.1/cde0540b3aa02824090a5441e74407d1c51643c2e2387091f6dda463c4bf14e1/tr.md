```
remove_frames!(stack::StackTrace, name::Symbol)
```

Bir `StackTrace` (bir `StackFrames` vektörü) ve bir fonksiyon adı (bir `Symbol`) alır ve belirtilen fonksiyon adıyla belirtilen `StackFrame`'i `StackTrace`'den kaldırır (belirtilen fonksiyonun üzerindeki tüm çerçeveleri de kaldırır). Öncelikle, `StackTrace`'i döndürmeden önce `StackTrace` fonksiyonlarını kaldırmak için kullanılır.
