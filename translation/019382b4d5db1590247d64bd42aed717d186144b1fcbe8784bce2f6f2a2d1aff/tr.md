```
download(url, [ output = tempname() ];
    [ method = "GET", ]
    [ headers = <none>, ]
    [ timeout = <none>, ]
    [ progress = <none>, ]
    [ verbose = false, ]
    [ debug = <none>, ]
    [ downloader = <default>, ]
) -> output

    url        :: AbstractString
    output     :: Union{AbstractString, AbstractCmd, IO}
    method     :: AbstractString
    headers    :: Union{AbstractVector, AbstractDict}
    timeout    :: Real
    progress   :: (total::Integer, now::Integer) --> Any
    verbose    :: Bool
    debug      :: (type, message) --> Any
    downloader :: Downloader
```

Verilen url'den bir dosya indirin, `output`'a kaydedin veya belirtilmemişse geçici bir yola kaydedin. `output` ayrıca bir `IO` handle'ı da olabilir, bu durumda yanıtın gövdesi o handle'a akıtılır ve handle döndürülür. Eğer `output` bir komutsa, komut çalıştırılır ve çıktı stdin'e gönderilir.

Eğer `downloader` anahtar argümanı sağlanmışsa, bu bir `Downloader` nesnesi olmalıdır. Kaynaklar ve bağlantılar, aynı `Downloader` tarafından gerçekleştirilen indirmeler arasında paylaşılacak ve nesne çöp toplandığında veya onunla hiçbir indirme gerçekleştirilmediğinde otomatik olarak temizlenecektir. Konfigürasyon ve kullanım hakkında daha fazla bilgi için `Downloader`'a bakın.

Eğer `headers` anahtar argümanı sağlanmışsa, bu tüm elemanları string çiftleri olan bir vektör veya sözlük olmalıdır. Bu çiftler, HTTP/S gibi bunları destekleyen protokollerle URL'leri indirirken başlıklar olarak geçilir.

`timeout` anahtar argümanı, indirmenin tamamlanması için saniye cinsinden bir zaman aşımını belirtir ve milisaniye çözünürlüğüne sahiptir. Varsayılan olarak zaman aşımı ayarlanmamıştır, ancak bu, `Inf` zaman aşımı değeri geçilerek açıkça talep edilebilir. Ayrıca, 20 saniye boyunca herhangi bir veri alınmazsa, indirme zaman aşımına uğrayacaktır. Bu zaman aşımını devre dışı bırakma hakkında daha fazla yardım için genişletilmiş yardıma bakın.

Eğer `progress` anahtar argmanı sağlanmışsa, bu, devam eden indirme hakkında boyut ve durum güncellemeleri olduğunda çağrılacak bir geri çağırma fonksiyonu olmalıdır. Geri çağırma, toplam indirme boyutu byte cinsinden `total` ve şu ana kadar indirilen byte sayısı `now` olmak üzere iki tam sayı argümanı almalıdır. `total` sıfırdan başlar ve sunucu toplam indirme boyutunun bir göstergesini verene kadar sıfır kalır (örneğin, bir `Content-Length` başlığı ile), bu asla olmayabilir. Bu nedenle, iyi davranan bir ilerleme geri çağırması, toplam boyutu sıfır olan durumları zarif bir şekilde ele almalıdır.

Eğer `verbose` seçeneği true olarak ayarlanmışsa, indirme işlevselliğini uygulamak için kullanılan `libcurl`, hata ayıklama bilgilerini `stderr`'ye yazdıracaktır. Eğer `debug` seçeneği iki `String` argümanı kabul eden bir fonksiyona ayarlanmışsa, o zaman ayrıntılı seçenek göz ardı edilir ve bunun yerine `stderr`'ye yazdırılacak olan veriler `type` ve `message` argümanları ile `debug` geri çağırmasına iletilir. `type` argümanı, hangi tür olayın meydana geldiğini belirtir ve şunlardan biridir: `TEXT`, `HEADER IN`, `HEADER OUT`, `DATA IN`, `DATA OUT`, `SSL DATA IN` veya `SSL DATA OUT`. `message` argümanı, hata ayıklama olayının tanımıdır.

## Genişletilmiş Yardım

Daha fazla özelleştirme için, bir [`Downloader`](@ref) ve [`easy_hook`s](https://github.com/JuliaLang/Downloads.jl#mutual-tls-using-downloads) kullanın. Örneğin, veri alınmadığında 20 saniyelik zaman aşımını devre dışı bırakmak için aşağıdakileri kullanabilirsiniz:

```jl
downloader = Downloads.Downloader()
downloader.easy_hook = (easy, info) -> Downloads.Curl.setopt(easy, Downloads.Curl.CURLOPT_LOW_SPEED_TIME, 0)

Downloads.download("https://httpbingo.julialang.org/delay/30"; downloader)
```
