```
dlopen(libfile::AbstractString [, flags::Integer]; throw_error:Bool = true)
```

Paylaşılan bir kütüphaneyi yükler ve opak bir handle döner.

Sabit `dlext` tarafından verilen uzantı (`.so`, `.dll` veya `.dylib)`libfile`dizesinden çıkarılabilir, çünkü gerekirse otomatik olarak eklenir. Eğer`libfile`mutlak bir yol adı değilse,`libfile`için`DL*LOAD*PATH` dizisindeki yollar aranır, ardından sistem yükleme yolu kontrol edilir.

İsteğe bağlı bayrak argümanı, sıfır veya daha fazla `RTLD_LOCAL`, `RTLD_GLOBAL`, `RTLD_LAZY`, `RTLD_NOW`, `RTLD_NODELETE`, `RTLD_NOLOAD`, `RTLD_DEEPBIND` ve `RTLD_FIRST` bayrağının bit düzeyinde veya işlemidir. Bunlar, mümkünse POSIX (ve/veya GNU libc ve/veya MacOS) dlopen komutunun karşılık gelen bayraklarına dönüştürülür veya belirtilen işlevsellik mevcut platformda mevcut değilse göz ardı edilir. Varsayılan bayraklar platforma özgüdür. MacOS'ta varsayılan `dlopen` bayrakları `RTLD_LAZY|RTLD_DEEPBIND|RTLD_GLOBAL` iken, diğer platformlarda varsayılanlar `RTLD_LAZY|RTLD_DEEPBIND|RTLD_LOCAL`'dır. Bu bayrakların önemli bir kullanımı, dinamik kütüphane yükleyicisinin kütüphane referanslarını dışa aktarılan sembollere bağladığında ve bağlı referansların işlem yerel veya küresel kapsamda olup olmadığını belirtmektir. Örneğin, `RTLD_LAZY|RTLD_DEEPBIND|RTLD_GLOBAL`, kütüphanenin sembollerinin diğer paylaşılan kütüphanelerde kullanılabilir olmasını sağlar ve paylaşılan kütüphaneler arasında bağımlılıkların olduğu durumları ele alır.

Eğer kütüphane bulunamazsa, bu yöntem bir hata fırlatır, `throw_error` anahtar kelime argümanı `false` olarak ayarlanmadıkça, bu durumda bu yöntem `nothing` döner.

!!! note
    Julia 1.6'dan itibaren, bu yöntem `@executable_path/` ile başlayan yolları Julia yürütülebilir dosyasının yolu ile değiştirir ve taşınabilir göreli yol yüklemelerine olanak tanır. Julia 1.5 ve öncesinde, bu yalnızca macOS'ta çalışıyordu.

