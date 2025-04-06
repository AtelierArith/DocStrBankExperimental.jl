```
clear_malloc_data()
```

`--track-allocation` ile julia çalıştırırken saklanan herhangi bir bellek tahsis verisini temizler. Test etmek istediğiniz komut(lar)ı çalıştırın (JIT derlemesini zorlamak için), ardından [`clear_malloc_data`](@ref) çağrısını yapın. Ardından komut(lar)ınızı tekrar çalıştırın, Julia'dan çıkın ve ortaya çıkan `*.mem` dosyalarını inceleyin.
