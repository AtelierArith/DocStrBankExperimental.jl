```
rewrite(
    [ predicate, ] eski_tarball, [ yeni_tarball ];
    [ taşınabilir = false, ]
) -> yeni_tarball

    predicate   :: Header --> Bool
    eski_tarball :: Union{AbstractString, AbstractCmd, IO}
    yeni_tarball :: Union{AbstractString, AbstractCmd, IO}
    taşınabilir    :: Bool
```

`eski_tarball`'ı `create`'in ürettiği standart formata yeniden yazarken, `extract`'in hata vermesine neden olabilecek herhangi bir şey içermediğinden emin olun. Bu, işlevsel olarak şuna eşdeğerdir:

```
Tar.create(Tar.extract(predicate, eski_tarball), yeni_tarball)
```

Ancak, hiçbir şeyi diske çıkarmadan, bunun yerine `eski_tarball`'ın verilerinde gezinmek için `seek` fonksiyonunu kullanır. Eğer bir `yeni_tarball` argümanı geçilmezse, yeni tarball geçici bir dosyaya yazılır ve bu dosyanın yolu döndürülür.

Eğer bir `predicate` fonksiyonu geçilirse, bu fonksiyon `eski_tarball`'ı çıkarırken karşılaşılan her `Header` nesnesi üzerinde çağrılır ve giriş, `predicate(hdr)` doğru olmadığı sürece atlanır. Bu, yalnızca bir arşivin belirli kısımlarını yeniden yazmak, `extract`'in hata vermesine neden olacak girişleri atlamak veya yeniden yazma sürecinde karşılaşılan içeriği kaydetmek için kullanılabilir.

`predicate` fonksiyonuna geçilmeden önce, `Header` nesnesi tarball'daki ham başlıktan biraz değiştirilir: `path` alanı, `.` girişlerini kaldıracak şekilde normalize edilir ve birden fazla ardışık eğik çizgi tek bir eğik çizgi ile değiştirilir. Eğer girişin türü `:hardlink` ise, bağlantı hedef yolu aynı şekilde normalize edilir, böylece hedef girişin yolu ile eşleşir; boyut alanı, hedef yolun boyutuna (bu, daha önce görülmüş bir dosya olmalıdır) ayarlanır.

Eğer `taşınabilir` bayrağı doğruysa, o zaman yol adları Windows'ta geçerlilik açısından kontrol edilir, bu da bunların yasaklı karakterler içermediğinden veya rezerve edilmiş adlar olmadığından emin olur. Detaylar için bkz. https://stackoverflow.com/a/31976060/659248.
