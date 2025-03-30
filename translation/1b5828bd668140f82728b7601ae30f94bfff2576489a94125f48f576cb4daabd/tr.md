# Handling Operating System Variation

Çapraz platform uygulamaları veya kütüphaneler yazarken, işletim sistemleri arasındaki farklılıklara izin vermek genellikle gereklidir. `Sys.KERNEL` değişkeni, bu tür durumları yönetmek için kullanılabilir. Bunu kolaylaştırmak amacıyla `Sys` modülünde `isunix`, `islinux`, `isapple`, `isbsd`, `isfreebsd` ve `iswindows` gibi birkaç işlev bulunmaktadır. Bunlar aşağıdaki gibi kullanılabilir:

```julia
if Sys.iswindows()
    windows_specific_thing(a)
end
```

`islinux`, `isapple` ve `isfreebsd`'nin `isunix`'in karşılıklı dışlayıcı alt kümeleri olduğunu unutmayın. Ayrıca, geçersiz kodu koşullu olarak gizlemek için bu işlevleri kullanmayı mümkün kılan `@static` adlı bir makro vardır; bu, aşağıdaki örneklerde gösterilmiştir.

Basit bloklar:

```
ccall((@static Sys.iswindows() ? :_fopen : :fopen), ...)
```

Karmaşık bloklar:

```julia
@static if Sys.islinux()
    linux_specific_thing(a)
elseif Sys.isapple()
    apple_specific_thing(a)
else
    generic_thing(a)
end
```

Koşullu ifadeleri iç içe yerleştirirken, `@static` her seviye için tekrarlanmalıdır (parantezler isteğe bağlıdır, ancak okunabilirlik için önerilir):

```julia
@static Sys.iswindows() ? :a : (@static Sys.isapple() ? :b : :c)
```
