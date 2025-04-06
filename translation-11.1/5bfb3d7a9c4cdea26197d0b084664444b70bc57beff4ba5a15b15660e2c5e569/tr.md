```
struct RequestError <: ErrorException
    url      :: String
    code     :: Int
    message  :: String
    response :: Response
end
```

`RequestError`, bir isteğe verilen başarısız yanıtın özelliklerini bir istisna nesnesi olarak yakalayan bir türdür:

  * `url`: yönlendirme olmadan talep edilen orijinal URL
  * `code`: libcurl hata kodu; yalnızca bir protokol hatası meydana geldiyse `0`
  * `message`: neyin yanlış gittiğini belirten libcurl hata mesajı
  * `response`: mevcut yanıt bilgilerini yakalayan yanıt nesnesi

Aynı `RequestError` türü, istek başarılı olsa bile, 2xx aralığında olmayan bir durum kodu ile gösterilen bir protokol düzeyi hatası varsa `download` tarafından fırlatılır; bu durumda `code` sıfır olacak ve `message` alanı boş bir dize olacaktır. `request` API'si yalnızca libcurl hata `code`'u sıfırdan farklı olduğunda bir `RequestError` fırlatır; bu durumda dahil edilen `response` nesnesinin muhtemelen sıfır bir `status` ve boş bir mesajı olacaktır. Ancak, bir protokol hatası nedeniyle bir curl düzeyi hatası fırlatılan durumlar da vardır; bu durumda hem iç hem de dış kod ve mesaj ilgi çekici olabilir.
