```
edit(path::AbstractString, line::Integer=0, column::Integer=0)
```

Bir dosyayı veya dizini düzenleyin, isteğe bağlı olarak dosyayı düzenlemek için bir satır numarası sağlayın. Düzenleyiciden çıktığınızda `julia` istemine geri dönün. Düzenleyici, bir ortam değişkeni olarak `JULIA_EDITOR`, `VISUAL` veya `EDITOR` ayarlanarak değiştirilebilir.

!!! uyumluluk "Julia 1.9"
    `column` argümanı en az Julia 1.9 gerektirir.


Ayrıca bkz. [`InteractiveUtils.define_editor`](@ref).
