```
pathof(m::Module)
```

`m` modülünü `import` etmek için kullanılan `m.jl` dosyasının yolunu döndürür veya `m` bir paket içinden import edilmemişse `nothing` döner.

Yolun dizin kısmını almak için [`dirname`](@ref) ve dosya adı kısmını almak için [`basename`](@ref) kullanın.

Ayrıca bkz. [`pkgdir`](@ref).
