```
Config(; scroll_wrap=false, ctrl_c_interrupt=true, charset=:ascii, cursor::Char, up_arrow::Char, down_arrow::Char)
```

Seçim menüleri için davranışı anahtar argümanlar aracılığıyla yapılandırın:

  * `scroll_wrap`, `true` ise, menünün ilk girişin üstünde veya son girişin altında kaydırıldığında etrafında dönmesini sağlar
  * `ctrl_c_interrupt`, `true` ise, kullanıcı menü seçimi sırasında Ctrl-C'ye basarsa bir `InterruptException` fırlatır. `false` ise, [`TerminalMenus.request`](@ref) [`TerminalMenus.selected`](@ref) ile varsayılan sonucu döndürecektir.
  * `charset`, `cursor`, `up_arrow` ve `down_arrow` için varsayılan değerleri etkiler ve `:ascii` veya `:unicode` olabilir
  * `cursor`, "Enter" tuşuna basarak seçilecek seçeneği göstermek için basılan karakterdir. Varsayılanlar `>` veya `→`'dir, `charset`'e bağlı olarak.
  * `up_arrow`, görüntü ilk girişi içermediğinde basılan karakterdir. Varsayılanlar `^` veya `↑`'dir, `charset`'e bağlı olarak.
  * `down_arrow`, görüntü son girişi içermediğinde basılan karakterdir. Varsayılanlar `v` veya `↓`'dir, `charset`'e bağlı olarak.

`ConfiguredMenu` alt türleri, gerektiğinde `cursor`, `up_arrow` ve `down_arrow`'ı otomatik olarak basacaktır, `writeline` yönteminiz bunları basmamalıdır.

!!! compat "Julia 1.6"
    `Config`, Julia 1.6 itibarıyla mevcuttur. Daha eski sürümlerde global `CONFIG`'i kullanın.

