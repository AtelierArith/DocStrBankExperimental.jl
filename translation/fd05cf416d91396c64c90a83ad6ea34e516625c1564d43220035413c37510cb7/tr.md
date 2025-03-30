```
list(tarball; [ strict = true ]) -> Vector{Header}
list(callback, tarball; [ strict = true ])

    callback  :: Header, [ <data> ] --> Any
    tarball   :: Union{AbstractString, AbstractCmd, IO}
    strict    :: Bool
```

Bir tar arşivinin ("tarball") içeriğini `tarball` yolunda bulunan bir arşivden listeleyin. Eğer `tarball` bir IO handle ise, tar içeriğini o akıştan okuyun. Bir `Header` yapılarının vektörünü döndürür. Ayrıntılar için [`Header`](@ref) bakın.

Eğer bir `callback` sağlanmışsa, o zaman başlıkların bir vektörünü döndürmek yerine, her `Header` üzerinde callback çağrılır. Bu, tarball'daki öğe sayısı büyükse veya bir hata öncesinde öğeleri incelemek istiyorsanız yararlı olabilir. Eğer `callback` fonksiyonu ikinci bir argüman olarak `Vector{UInt8}` veya `Vector{Pair{Symbol, String}}` türlerinden birini kabul edebiliyorsa, o zaman bu, alan adlarını o alanın ham verisi ile eşleyen çiftlerin vektörü veya tek bir bayt vektörü olarak ham başlık verisinin bir temsili ile çağrılacaktır (eğer bu alanlar bir araya getirilirse, sonuç başlığın ham verisidir).

Varsayılan olarak `list`, `extract` fonksiyonunun çıkarmayı reddedeceği herhangi bir tarball içeriği ile karşılaşırsa hata verecektir. `strict=false` ile bu kontrolleri atlayacak ve `extract` bunları çıkarır mı çıkarmaz mı bakılmaksızın tar dosyasının tüm içeriğini listeleyecektir. Kötü niyetli tarball'ların sizi kötü bir şey yapmaya ikna etmek için her türlü kurnaz ve beklenmedik şey yapabileceğini unutmayın.

Eğer `tarball` argümanı bir iskelet dosyası ise (bkz. `extract` ve `create`), o zaman `list` dosya başlığından bunu tespit edecek ve iskelet dosyasının başlıklarını uygun şekilde listeleyecek veya yineleyecektir.
