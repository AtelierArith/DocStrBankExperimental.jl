```
unsafe_copyto!(dest::Array, do, src::Array, so, N)
```

Bir kaynak diziden bir hedefe `N` eleman kopyalayın, kaynakta `so` ve hedefte `do` doğrusal indeksinden başlayarak (1-indeksli).

Bu işlevdeki `unsafe` ön eki, N'nin her iki dizide de sınır içinde olduğunu doğrulamak için hiçbir doğrulama yapılmadığını gösterir. Yanlış kullanım, programınızı C'de olduğu gibi bozulmasına veya segfault'a neden olabilir.
