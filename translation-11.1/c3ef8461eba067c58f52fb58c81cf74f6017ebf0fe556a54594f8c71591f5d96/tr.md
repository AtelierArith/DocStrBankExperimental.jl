```
fetch(repo::GitRepo; kwargs...)
```

Depo `repo`'nun yukarı akışından güncellemeleri alır.

Anahtar argümanlar şunlardır:

  * `remote::AbstractString="origin"`: `repo`'dan alınacak olan, adıyla belirtilen uzak. Bu boşsa, URL anonim bir uzak oluşturmak için kullanılacaktır.
  * `remoteurl::AbstractString=""`: `remote`'un URL'si. Belirtilmezse, `remote`'un verilen adı temel alınarak varsayılacaktır.
  * `refspecs=AbstractString[]`: alımın özelliklerini belirler.
  * `credentials=nothing`: özel bir `remote`'a karşı kimlik doğrularken kimlik bilgileri ve/veya ayarlar sağlar.
  * `callbacks=Callbacks()`: kullanıcı tarafından sağlanan geri çağırmalar ve yükler.

`git fetch [<remoteurl>|<repo>] [<refspecs>]` ile eşdeğerdir.
