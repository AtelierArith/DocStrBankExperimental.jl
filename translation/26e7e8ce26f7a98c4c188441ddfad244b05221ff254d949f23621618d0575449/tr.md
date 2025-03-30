```
MultiSelectConfig(; charset=:ascii, checked::String, unchecked::String, kwargs...)
```

Birden fazla seçim menüsünün davranışını anahtar kelime argümanları aracılığıyla yapılandırın:

  * `checked`, bir seçeneğin seçildiğinde yazdırılacak dizedir. Varsayılanlar `"[X]"` veya `"✓"` olup, `charset`'e bağlıdır.
  * `unchecked`, bir seçeneğin seçilmediğinde yazdırılacak dizedir. Varsayılanlar `"[ ]"` veya `"⬚"` olup, `charset`'e bağlıdır.

Diğer tüm anahtar kelime argümanları [`TerminalMenus.Config`](@ref) için tanımlandığı gibidir. `checked` ve `unchecked` otomatik olarak yazdırılmaz ve `writeline` yönteminiz tarafından yazdırılmalıdır.

!!! compat "Julia 1.6"
    `MultiSelectConfig`, Julia 1.6 itibarıyla mevcuttur. Daha eski sürümlerde global `CONFIG`'i kullanın.

