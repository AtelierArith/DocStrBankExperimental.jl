```
push(repo::GitRepo; kwargs...)
```

`repo`'nun bir üst akışına güncellemeleri gönderir.

Anahtar kelime argümanları şunlardır:

  * `remote::AbstractString="origin"`: gönderilecek üst akış uzaktan adıdır.
  * `remoteurl::AbstractString=""`: `remote`'un URL'sidir.
  * `refspecs=AbstractString[]`: gönderimin özelliklerini belirler.
  * `force::Bool=false`: gönderimin zorla gönderim olup olmayacağını belirler, uzaktan dalı üzerine yazar.
  * `credentials=nothing`: özel bir `remote` ile kimlik doğrularken kimlik bilgileri ve/veya ayarlar sağlar.
  * `callbacks=Callbacks()`: kullanıcı tarafından sağlanan geri çağırmalar ve yükler.

`git push [<remoteurl>|<repo>] [<refspecs>]` ile eşdeğerdir.
