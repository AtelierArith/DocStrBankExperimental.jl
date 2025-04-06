```
unwatch_folder(path::AbstractString)
```

`path` için değişikliklerin arka planda izlenmesini durdurur. Aynı `path` üzerinde `watch_folder`'ın dönmesini bekleyen başka bir görev varken bunu yapmanız önerilmez, çünkü sonuç öngörülemez olabilir.
