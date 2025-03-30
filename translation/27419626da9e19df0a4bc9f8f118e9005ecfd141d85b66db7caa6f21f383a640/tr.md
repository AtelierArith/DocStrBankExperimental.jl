```
cp(src::AbstractString, dst::AbstractString; force::Bool=false, follow_symlinks::Bool=false)
```

`src`'den `dst`'ye dosyayı, bağlantıyı veya dizini kopyalayın. `force=true` mevcut bir `dst`'yi önce kaldıracaktır.

Eğer `follow_symlinks=false` ise ve `src` bir sembolik bağlantıysa, `dst` bir sembolik bağlantı olarak oluşturulacaktır. Eğer `follow_symlinks=true` ve `src` bir sembolik bağlantıysa, `dst`, `src`'nin referans verdiği dosyanın veya dizinin bir kopyası olacaktır. `dst`'yi döndürün.

!!! note
    `cp` fonksiyonu `cp` komutundan farklıdır. `cp` fonksiyonu her zaman `dst`'nin bir dosya olduğu varsayımıyla çalışır, oysa komut `dst`'nin bir dizin mi yoksa bir dosya mı olduğuna bağlı olarak farklı şeyler yapar. `dst` bir dizin olduğunda `force=true` kullanmak, `dst` dizininde mevcut olan tüm içeriklerin kaybına yol açacak ve `dst`, `src`'nin içeriklerini barındıran bir dosya haline gelecektir.

