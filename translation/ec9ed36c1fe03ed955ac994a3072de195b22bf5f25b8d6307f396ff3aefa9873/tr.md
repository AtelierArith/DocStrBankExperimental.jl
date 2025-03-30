```
verilen url'ye bir istek yapın ve yanıtın durumu, başlıkları ve diğer bilgileri yakalayan bir `Response` nesnesi döndürün. Yanıtın gövdesi, belirtilmişse `output`'a yazılır, aksi takdirde atılır. HTTP/S istekleri için, bir `input` akışı verilmişse, bir `PUT` isteği yapılır; aksi takdirde bir `output` akışı verilmişse, bir `GET` isteği yapılır; eğer ikisi de verilmemişse bir `HEAD` isteği yapılır. Diğer protokoller için, istenen giriş ve çıkış kombinasyonuna dayalı olarak uygun varsayılan yöntemler kullanılır. Aşağıdaki seçenekler `download` işlevinden farklıdır:

  * `input`, bir istek gövdesi sağlamaya olanak tanır; sağlanırsa varsayılan olarak `PUT` isteğine geçer
  * `progress`, yükleme ve indirme ilerlemesi için dört tam sayı alan bir geri çağırmadır
  * `throw`, istek hatası durumunda bir `RequestError` fırlatılıp fırlatılmayacağını kontrol eder

`download`'ın aksine, istenen URL indirilemediğinde (2xx dışı durum kodu ile gösterilir) bir hata fırlatırken, `request` yanıtın durum kodu ne olursa olsun bir `Response` nesnesi döndürür. Eğer bir yanıt almakta bir hata varsa, o zaman bir `RequestError` fırlatılır veya döndürülür.

`interrupt` anahtar argümanı sağlanırsa, bir `Base.Event` nesnesi olmalıdır. İstek devam ederken olay tetiklenirse, istek iptal edilir ve bir hata fırlatılır. Bu, örneğin kullanıcının bir indirmeyi iptal etmek istemesi durumunda uzun süren bir isteği kesmek için kullanılabilir.
```
