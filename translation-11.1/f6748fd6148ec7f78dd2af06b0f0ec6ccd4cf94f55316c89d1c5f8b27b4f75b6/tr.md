```
addenv(command::Cmd, env...; inherit::Bool = true)
```

Yeni ortam eşlemelerini verilen [`Cmd`](@ref) nesnesine birleştirir ve yeni bir `Cmd` nesnesi döndürür. Tekrar eden anahtarlar değiştirilir. Eğer `command` zaten herhangi bir ortam değeri içermiyorsa, `inherit` `true` ise `addenv()` çağrısı sırasında mevcut ortamı miras alır. Değeri `nothing` olan anahtarlar ortamdan silinir.

Ayrıca bkz. [`Cmd`](@ref), [`setenv`](@ref), [`ENV`](@ref).

!!! compat "Julia 1.6"
    Bu fonksiyon Julia 1.6 veya daha yenisini gerektirir.

