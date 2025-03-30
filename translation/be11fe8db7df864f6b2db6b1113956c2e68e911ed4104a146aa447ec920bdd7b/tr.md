```
include_dependency(path::AbstractString; track_content::Bool=true)
```

Bir modülde, `path` (göreceli veya mutlak) ile belirtilen dosyanın, dizinin veya sembolik bağlantının ön derleme için bir bağımlılık olduğunu belirtin; yani, `track_content=true` ise, `path`'in içeriği değişirse modülün yeniden derlenmesi gerekecektir (eğer `path` bir dizin ise içerik `join(readdir(path))` ile eşittir). Eğer `track_content=false` ise, yeniden derleme, `path`'in değişiklik zamanı `mtime` değiştiğinde tetiklenir.

Bu, modülünüzün [`include`](@ref) aracılığıyla kullanılmayan bir yola bağımlı olması durumunda yalnızca gereklidir. Derleme dışında hiçbir etkisi yoktur.

!!! compat "Julia 1.11"
    Anahtar argüman `track_content`, en az Julia 1.11 gerektirir. `path` okunabilir değilse artık bir hata fırlatılır.

