```
mkpidlock([f::Function], at::String, [pid::Cint]; kwopts...)
mkpidlock(at::String, proc::Process; kwopts...)
```

Mevcut işlem veya pid veya proc ile tanımlanan işlem için "at" yolunda bir pidfile kilidi oluşturur. Kilit açıldığında çalıştırılacak bir işlev alabilir, bu da `do` bloklarında kullanım için geçerlidir; ardından kilit otomatik olarak kapatılacaktır. Kilit başarısız olursa ve `wait` false ise, bir hata fırlatılır.

Kilit, ya `close`, bir `finalizer` veya `proc` çıkış yaptıktan kısa bir süre sonra serbest bırakılacaktır. Dönüş değerinin programınızın kritik bölümünün sonuna kadar canlı olduğundan emin olun, böylece `finalizer` onu erken geri almaz.

İsteğe bağlı anahtar argümanlar:

  * `mode`: dosya erişim modu (işlem umask'ı tarafından değiştirilir). Varsayılan olarak dünya tarafından okunabilir.
  * `poll_interval`: Denemeler arasındaki maksimum süreyi belirtin (eğer `watch_file` çalışmazsa)
  * `stale_age`: Mevcut bir pidfile'ı (kilidi göz ardı ederek) bu kadar saniye daha eskiyse silin. Dosya, dosyadaki pid geçerli görünüyor gibi görünüyorsa, bu süreden 5 kat daha uzun süre silinmeyecektir. Veya `refresh` 0 olarak geçersiz kılınırsa kilit yenilemesi devre dışı bırakılırsa 25 kat daha uzun süre. Varsayılan olarak bu devre dışı bırakılmıştır (`stale_age` = 0), ancak tipik olarak önerilen bir değer, tahmini normal tamamlama süresinin yaklaşık 3-5 katı olacaktır.
  * `refresh`: Kilidin bayatlamasını önlemek için geçen her zaman aralığında mtime'ı güncelleyerek. Varsayılan olarak, bu `stale_age/2` olarak ayarlanmıştır, bu da önerilen değerdir.
  * `wait`: Eğer true ise, kilidi alana kadar engelle, false ise, kilit başarısız olursa hata fırlat.
