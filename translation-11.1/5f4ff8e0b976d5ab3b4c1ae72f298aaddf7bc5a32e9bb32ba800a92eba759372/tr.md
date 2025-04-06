```
using
```

`using Foo` modül veya paket `Foo`'yu yükleyecek ve onun [`export`](@ref) edilmiş isimlerini doğrudan kullanım için erişilebilir hale getirecektir. İsimler, `export` edilmiş olsun ya da olmasın, nokta sözdizimi ile de kullanılabilir (örneğin, `Foo.foo` ile `foo` ismine erişmek için). Ayrıntılar için [modüller hakkında kılavuz bölümüne](@ref modules) bakın.

!!! note
    İki veya daha fazla paket/modül bir ismi `export` ediyorsa ve bu isim her bir pakette aynı şeye atıfta bulunmuyorsa, ve paketler `using` ile açık bir isim listesi olmadan yükleniyorsa, o isme nitelik olmadan atıfta bulunmak bir hata olacaktır. Bu nedenle, bağımlılıklarının ve Julia'nın gelecekteki sürümleriyle ileriye dönük uyumlu olması amaçlanan kodların, örneğin, yayımlanan paketlerde, her yüklenen paketten kullandığı isimleri listelemesi önerilir; örneğin, `using Foo: Foo, f` yerine `using Foo` kullanmak.

