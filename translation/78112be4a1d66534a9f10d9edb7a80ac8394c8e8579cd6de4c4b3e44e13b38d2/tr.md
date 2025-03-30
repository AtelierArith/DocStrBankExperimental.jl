```
create(
    [ predicate, ] dir, [ tarball ];
    [ skeleton, ] [ portable = false ]
) -> tarball

    predicate :: String --> Bool
    dir       :: AbstractString
    tarball   :: Union{AbstractString, AbstractCmd, IO}
    skeleton  :: Union{AbstractString, AbstractCmd, IO}
    portable  :: Bool
```

`dir` dizininde bir tar arşivi ("tarball") oluşturun. Ortaya çıkan arşiv, `tarball` yoluna yazılır veya eğer bir yol belirtilmemişse, geçici bir yol oluşturulur ve fonksiyon çağrısı ile döndürülür. Eğer `tarball` bir IO nesnesi ise, tarball içeriği o handle'a yazılır (handle açık kalır).

Bir `predicate` fonksiyonu geçilirse, bu fonksiyon `dir` içinde özyinelemeli olarak arama yapılırken karşılaşılan her sistem yolu üzerinde çağrılır ve yalnızca `predicate(path)` doğruysa `path` tarball'a dahil edilir. Eğer `predicate(path)` bir dizin için yanlış dönerse, o dizin tamamen hariç tutulur: o dizin altındaki hiçbir şey arşive dahil edilmez.

`skeleton` anahtarı geçilirse, verilen dosya veya IO handle, tarball oluşturmak için bir "iskelet" olarak kullanılır. Bir iskelet dosyası oluşturmak için `extract` komutuna `skeleton` anahtarını geçersiniz. Eğer `create` o iskelet dosyası ile çağrılırsa ve çıkarılan dosyalar değişmemişse, aynı tarball yeniden oluşturulur. `skeleton` ve `predicate` argümanları birlikte kullanılamaz.

`portable` bayrağı doğruysa, yol adları Windows'ta geçerlilik açısından kontrol edilir; bu, geçersiz karakterler içermediğinden veya rezerve edilmiş adlar olmadığından emin olur. Ayrıntılar için https://stackoverflow.com/a/31976060/659248 adresine bakın.
