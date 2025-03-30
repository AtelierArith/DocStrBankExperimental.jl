```
redirect_stdin(f::Function, stream)
```

`f` fonksiyonunu `stream`'e yönlendirerek çalıştırır. Tamamlandığında, [`stdin`](@ref) önceki ayarına geri döner.
