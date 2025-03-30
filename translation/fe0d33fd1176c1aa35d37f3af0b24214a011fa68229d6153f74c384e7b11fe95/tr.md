```
Base.compilecache(module::PkgId)
```

Bir modül ve tüm bağımlılıkları için önceden derlenmiş bir önbellek dosyası oluşturur. Bu, paket yükleme sürelerini azaltmak için kullanılabilir. Önbellek dosyaları `DEPOT_PATH[1]/compiled` içinde saklanır. Önemli notlar için [Modül başlatma ve ön derleme](@ref) kısmına bakın.
