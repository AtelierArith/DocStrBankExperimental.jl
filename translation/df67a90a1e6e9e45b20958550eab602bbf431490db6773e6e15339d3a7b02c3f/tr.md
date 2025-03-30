```
redirect_stderr(f::Function, stream)
```

Fonksiyonu `f`'yi çalıştırırken [`stderr`](@ref) akışına yönlendirir. Tamamlandığında, [`stderr`](@ref) önceki ayarına geri döner.
