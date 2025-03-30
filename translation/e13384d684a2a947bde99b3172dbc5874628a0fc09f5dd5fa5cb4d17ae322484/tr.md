# Talking to the compiler (the `:meta` mechanism)

Bazı durumlarda, belirli bir kod bloğunun özel özelliklere sahip olduğunu belirtmek için ipuçları veya talimatlar vermek isteyebilirsiniz: her zaman iç içe almak isteyebilir veya özel derleyici optimizasyon geçişlerini etkinleştirmek isteyebilirsiniz. 0.4 sürümünden itibaren, Julia'nın bu talimatların genellikle (ama zorunlu olarak değil) bir fonksiyonun gövdesindeki ilk ifade olan `:meta` ifadesi içine yerleştirilebileceğine dair bir kuralı vardır.

`:meta` ifadeleri makrolarla oluşturulur. Örnek olarak, `@inline` makrosunun uygulanışını düşünün:

```julia
macro inline(ex)
    esc(isa(ex, Expr) ? pushmeta!(ex, :inline) : ex)
end
```

Burada, `ex` bir fonksiyonu tanımlayan bir ifade olarak beklenmektedir. Böyle bir ifade:

```julia
@inline function myfunction(x)
    x*(x+3)
end
```

bir ifade haline dönüşür:

```julia
quote
    function myfunction(x)
        Expr(:meta, :inline)
        x*(x+3)
    end
end
```

`Base.pushmeta!(ex, tag::Union{Symbol,Expr})` `:tag`'ı `:meta` ifadesinin sonuna ekler, gerekirse yeni bir `:meta` ifadesi oluşturur.

Meta verilerini kullanmak için bu `:meta` ifadelerini ayrıştırmanız gerekir. Uygulamanız Julia içinde gerçekleştirilebiliyorsa, `Base.popmeta!` oldukça kullanışlıdır: `Base.popmeta!(body, :symbol)` bir fonksiyon *body* ifadesini (fonksiyon imzası olmayan) `:symbol` içeren ilk `:meta` ifadesini tarar, herhangi bir argümanı çıkarır ve `(found::Bool, args::Array{Any})` şeklinde bir demet döner. Eğer meta verilerinin herhangi bir argümanı yoksa veya `:symbol` bulunamazsa, `args` dizisi boş olacaktır.

Henüz sağlanmamış bir altyapı, C++'dan `:meta` ifadelerini ayrıştırmak için uygundur.
