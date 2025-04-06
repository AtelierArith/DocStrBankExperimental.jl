```
Downloader(; [ grace::Gerçek = 30 ])
```

`Downloader` nesneleri, bireysel `download` işlemlerini gerçekleştirmek için kullanılır. Bağlantılar, ad aramaları ve diğer kaynaklar bir `Downloader` içinde paylaşılır. Bu bağlantılar ve kaynaklar, onunla bir şey indirildiğinden itibaren yapılandırılabilir bir grace süresi (varsayılan: 30 saniye) sonra veya çöp toplayıcı tarafından temizlendiğinde, hangisi önce gelirse, temizlenir. Grace süresi sıfıra ayarlanırsa, devam eden indirme işlemi kalmadığında tüm kaynaklar hemen temizlenecektir. Grace süresi `Inf` olarak ayarlanırsa, kaynaklar `Downloader` çöp toplayıcı tarafından temizlenene kadar temizlenmez.
