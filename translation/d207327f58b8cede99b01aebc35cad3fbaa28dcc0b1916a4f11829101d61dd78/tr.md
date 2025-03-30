```
struct Response
    proto   :: String
    url     :: String
    status  :: Int
    message :: String
    headers :: Vector{Pair{String,String}}
end
```

`Response` bir isteğe başarılı bir yanıtın özelliklerini bir nesne olarak yakalayan bir türdür. Aşağıdaki alanlara sahiptir:

  * `proto`: yanıtı almak için kullanılan protokol
  * `url`: yönlendirmeleri takip ettikten sonra nihayetinde istenen URL
  * `status`: yanıtın durum kodu, başarı, başarısızlık vb. durumları belirtir.
  * `message`: yanıtın niteliğini tanımlayan bir metin mesajı
  * `headers`: yanıtla birlikte dönen herhangi bir başlık

Bu yanıtların bazılarının anlamı ve kullanılabilirliği, istekte kullanılan protokole bağlıdır. HTTP/S ve S/FTP dahil birçok protokolde, 2xx durum kodu başarılı bir yanıtı belirtir. Başlıkları desteklemeyen protokollerdeki yanıtlar için başlıklar vektörü boş olacaktır. HTTP/2, yalnızca bir durum kodu içerir, durum mesajı içermez, bu nedenle mesaj boş olacaktır.
