```
Core.set_binding_type!(module::Module, name::Symbol, [type::Type])
```

Modül `module` içindeki `name` bağlamasının belirtilen türünü `type` olarak ayarlayın. Eğer bağlama zaten `type` ile eşdeğer olmayan bir türe sahipse hata verin. Eğer `type` argümanı yoksa, bağlama türünü ayarlanmamışsa `Any` olarak ayarlayın, ancak hata vermeyin.

!!! compat "Julia 1.9"
    Bu fonksiyon Julia 1.9 veya daha yenisini gerektirir.

