```
config( <gör argümanları> )
```

Küçük anahtar kelime işlevi, küresel menü parametrelerini yapılandırmak için

# Argümanlar

  * `charset::Symbol=:na`: kullanılacak ui karakterleri (`:ascii` veya `:unicode`); diğer argümanlar tarafından geçersiz kılınır
  * `cursor::Char='>'|'→'`: imleç için kullanılacak karakter
  * `up_arrow::Char='^'|'↑'`: yukarı ok için kullanılacak karakter
  * `down_arrow::Char='v'|'↓'`: aşağı ok için kullanılacak karakter
  * `checked::String="[X]"|"✓"`: işaretli için kullanılacak dize
  * `unchecked::String="[ ]"|"⬚")`: işaretsiz için kullanılacak dize
  * `scroll::Symbol=:nowrap`: Eğer `:wrap` ise imleci üst ve alt etrafında sar, eğer :`nowrap` ise imleci sarmayın
  * `supress_output::Bool=false`: Geçersiz kılınan eski argüman, bunun yerine `request`'e anahtar kelime argümanı olarak `suppress_output` geçirin.
  * `ctrl_c_interrupt::Bool=true`: Eğer `false` ise ^C'de boş döner, eğer `true` ise ^C'de InterruptException() fırlatır

!!! uyumluluk "Julia 1.6"
    Julia 1.6 itibarıyla, `config` kullanımdan kaldırılmıştır. Bunun yerine `Config` veya `MultiSelectConfig` kullanın.

