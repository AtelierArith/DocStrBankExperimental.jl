```
Experimental.register_error_hint(handler, exceptiontype)
```

Bir "ipucu" fonksiyonu `handler(io, exception)` kaydedin, bu fonksiyon kullanıcıların hataları aşmalarına yönelik potansiyel yollar önerebilir. `handler`, `exception`'ı incelemeli ve bir ipucu için uygun koşulların karşılanıp karşılanmadığını kontrol etmeli, eğer öyleyse `io`'ya çıktı üretmelidir. Paketler, `__init__` fonksiyonları içinde `register_error_hint` çağırmalıdır.

Belirli istisna türleri için, `handler`'ın ek argümanlar alması gerekmektedir:

  * `MethodError`: `handler(io, exc::MethodError, argtypes, kwargs)` sağlayın, bu, birleştirilmiş argümanları konumsal ve anahtar kelime argümanlarına ayırır.

Bir ipucu verildiğinde, çıktı genellikle `\n` ile başlamalıdır.

Özel istisna türleri tanımlarsanız, `showerror` metodunuz ipuçlarını [`Experimental.show_error_hints`](@ref) çağırarak destekleyebilir.

# Örnekler

```
julia> module Hinter

       only_int(x::Int)      = 1
       any_number(x::Number) = 2

       function __init__()
           Base.Experimental.register_error_hint(MethodError) do io, exc, argtypes, kwargs
               if exc.f == only_int
                    # Renk gerekli değildir, bu sadece mümkün olduğunu göstermek içindir.
                    print(io, "\nAcaba çağırmak mı istediniz ")
                    printstyled(io, "`any_number`?", color=:cyan)
               end
           end
       end

       end
```

Sonra `Hinter.only_int`'i bir `Int` olmayan bir şeyle çağırırsanız (böylece bir `MethodError` tetiklenir), ipucu verir:

```
julia> Hinter.only_int(1.0)
HATA: MethodError: no method matching only_int(::Float64)
`only_int` fonksiyonu mevcut, ancak bu argüman türleri kombinasyonu için tanımlı bir yöntem yok.
Acaba `any_number` mı çağırmak istediniz?
En yakın adaylar:
    ...
```

!!! uyumluluk "Julia 1.5"
    Özel hata ipuçları Julia 1.5 itibarıyla mevcuttur.


!!! uyarı     Bu arayüz deneysel olup, bildirimde bulunmaksızın değişikliklere veya kaldırmalara tabi olabilir. Değişikliklere karşı kendinizi korumak için, herhangi bir kaydı `if isdefined(Base.Experimental, :register_error_hint) ... end` bloğu içine koymayı düşünün.
