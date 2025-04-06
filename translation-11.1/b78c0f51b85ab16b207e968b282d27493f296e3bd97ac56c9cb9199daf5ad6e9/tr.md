```
remoteref_id(r::AbstractRemoteRef) -> RRID
```

`Future`lar ve `RemoteChannel`lar alanlarla tanımlanır:

  * `where` - referansla belirtilen temel nesnenin/depolamanın gerçekten bulunduğu düğümü ifade eder.
  * `whence` - uzak referansın oluşturulduğu düğümü ifade eder. Bu, referansla belirtilen temel nesnenin gerçekten bulunduğu düğümden farklıdır. Örneğin, ana süreçten `RemoteChannel(2)` çağrıldığında `where` değeri 2 ve `whence` değeri 1 olur.
  * `id`, `whence` ile belirtilen işçi tarafından oluşturulan tüm referanslar arasında benzersizdir.

Bir araya getirildiğinde, `whence` ve `id` tüm işçiler arasında bir referansı benzersiz şekilde tanımlar.

`remoteref_id`, bir uzak referansın `whence` ve `id` değerlerini saran bir `RRID` nesnesi döndüren düşük seviyeli bir API'dir.
