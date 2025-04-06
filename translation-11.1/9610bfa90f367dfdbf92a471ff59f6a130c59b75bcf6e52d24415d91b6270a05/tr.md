```
atreplinit(f)
```

Etkileşimli oturumlarda REPL arayüzü başlatılmadan önce çağrılacak bir tek argümanlı fonksiyonu kaydeder; bu, arayüzü özelleştirmek için yararlıdır. `f`'nin argümanı REPL nesnesidir. Bu fonksiyon, `.julia/config/startup.jl` başlatma dosyasının içinden çağrılmalıdır.
