```
redirect_stdout(f::Function, stream)
```

`f` fonksiyonunu çalıştırırken [`stdout`](@ref) akışını `stream`'e yönlendirin. Tamamlandığında, [`stdout`](@ref) önceki ayarına geri döner.
