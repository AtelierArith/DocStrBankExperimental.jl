```
ENV
```

Singleton `EnvDict`'e referans, sistem ortam değişkenlerine bir sözlük arayüzü sağlar.

(Windows'ta, sistem ortam değişkenleri büyük/küçük harf duyarsızdır ve `ENV` buna karşılık olarak tüm anahtarları görüntüleme, yineleme ve kopyalama için büyük harfe dönüştürür. Taşınabilir kod, değişkenleri büyük/küçük harf ile ayırt etme yeteneğine güvenmemeli ve görünüşte küçük harfli bir değişken ayarlamanın büyük harfli bir `ENV` anahtarı ile sonuçlanabileceğine dikkat etmelidir.)

!!! uyarı     Ortamı değiştirmek thread-safe değildir.

# Örnekler

```julia-repl
julia> ENV
Base.EnvDict with "50" entries:
  "SECURITYSESSIONID"            => "123"
  "USER"                         => "username"
  "MallocNanoZone"               => "0"
  ⋮                              => ⋮

julia> ENV["JULIA_EDITOR"] = "vim"
"vim"

julia> ENV["JULIA_EDITOR"]
"vim"
```

Ayrıca bakınız: [`withenv`](@ref), [`addenv`](@ref).
