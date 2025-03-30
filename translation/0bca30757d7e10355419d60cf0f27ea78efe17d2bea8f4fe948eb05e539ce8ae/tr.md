```
unsafe_copyto!(dest::Ptr{T}, src::Ptr{T}, N)
```

`N` elemanı bir kaynak işaretçisinden bir hedefe kopyalar, kontrol olmadan. Bir elemanın boyutu işaretçilerin türü tarafından belirlenir.

Bu işlevdeki `unsafe` ön eki, `dest` ve `src` işaretçileri üzerinde geçerliliği sağlamak için hiçbir doğrulama yapılmadığını gösterir. Yanlış kullanım, programınızı C'deki gibi bozulmasına veya segfault olmasına neden olabilir.
