```
extract(
    [ predicate, ] tarball, [ dir ];
    [ skeleton = <none>, ]
    [ copy_symlinks = <auto>, ]
    [ set_permissions = true, ]
) -> dir

    predicate       :: Header --> Bool
    tarball         :: Union{AbstractString, AbstractCmd, IO}
    dir             :: AbstractString
    skeleton        :: Union{AbstractString, AbstractCmd, IO}
    copy_symlinks   :: Bool
    set_permissions :: Bool
```

Bir tar arşivini ("tarball") `tarball` yolunda bulunan dizine `dir` çıkartın. Eğer `tarball` bir IO nesnesi ise, arşiv içeriği bu IO akışından okunacaktır. Arşiv, mevcut boş bir dizine veya yeni bir dizin olarak oluşturulabilecek var olmayan bir yola `dir` çıkartılır. Eğer `dir` belirtilmemişse, arşiv geçici bir dizine çıkartılır ve bu dizin `extract` tarafından döndürülür.

Eğer bir `predicate` fonksiyonu geçilmişse, bu fonksiyon `tarball` çıkarılırken karşılaşılan her `Header` nesnesi üzerinde çağrılır ve yalnızca `predicate(hdr)` doğruysa giriş çıkarılır. Bu, yalnızca bir arşivin belirli kısımlarını seçerek çıkartmak, `extract`'in hata fırlatmasına neden olan girişleri atlamak veya çıkarma işlemi sırasında neyin çıkarıldığını kaydetmek için kullanılabilir.

`Header` nesnesi, arşivdeki ham başlıktan biraz değiştirilerek geçilir: `path` alanı, `.` girişlerini kaldırmak ve birden fazla ardışık eğik çizgiyi tek bir eğik çizgi ile değiştirmek için normalize edilir. Giriş `:hardlink` türündeyse, bağlantı hedef yolu aynı şekilde normalize edilir, böylece hedef girişin yolu ile eşleşir; boyut alanı, hedef yolun boyutuna (zaten görülmüş bir dosya olmalıdır) ayarlanır.

Eğer `skeleton` anahtarı geçilmişse, çıkarılan tarball'ın bir "iskeleti" verilen dosyaya veya IO tutucusuna yazılır. Bu iskelet dosyası, `create` fonksiyonuna `skeleton` anahtarını geçerek özdeş bir tarball'ı yeniden oluşturmak için kullanılabilir. `skeleton` ve `predicate` argümanları birlikte kullanılamaz.

Eğer `copy_symlinks` `true` ise, sembolik bağlantılar olduğu gibi çıkarılmak yerine, iç tarball'a aitlerse ve bunu yapmak mümkünse, bağlantıların gösterdiği şeylerin kopyaları olarak çıkarılacaktır. `/etc/passwd` gibi iç olmayan sembolik bağlantılar kopyalanmayacaktır. Herhangi bir şekilde döngüsel olan sembolik bağlantılar da kopyalanmayacak ve bunun yerine atlanacaktır. Varsayılan olarak, `extract`, `dir` içinde sembolik bağlantıların oluşturulup oluşturulamayacağını tespit eder ve eğer oluşturulamazlarsa otomatik olarak sembolik bağlantıları kopyalar.

Eğer `set_permissions` `false` ise, çıkarılan dosyalar üzerinde hiçbir izin ayarlanmaz.
