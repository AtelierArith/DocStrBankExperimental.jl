```
@debug mesaj  [anahtar=değer | değer ...]
@info  mesaj  [anahtar=değer | değer ...]
@warn  mesaj  [anahtar=değer | değer ...]
@error mesaj  [anahtar=değer | değer ...]

@logmsg seviye mesaj [anahtar=değer | değer ...]

Bilgilendirici bir `mesaj` ile bir log kaydı oluşturun. Kolaylık olması açısından, `Debug`, `Info`, `Warn` ve `Error` standart ciddiyet seviyelerinde log kaydı yapan dört logging makrosu `@debug`, `@info`, `@warn` ve `@error` tanımlanmıştır. `@logmsg`, `seviye`nin programatik olarak herhangi bir `LogLevel` veya özel log seviye türlerine ayarlanmasına olanak tanır.

`mesaj`, log olayının insan tarafından okunabilir bir tanımını içeren bir dizeye değerlendirilmesi gereken bir ifadedir. Geleneksel olarak, bu dize sunulduğunda markdown olarak biçimlendirilir.

İsteğe bağlı `anahtar=değer` çiftleri listesi, log kaydının bir parçası olarak loglama arka ucuna iletilecek key-value çiftleri için kullanıcı tanımlı meta verileri destekler. Sadece bir `değer` ifadesi sağlanırsa, ifade için bir anahtar [`Symbol`](@ref) kullanılarak oluşturulacaktır. Örneğin, `x` `x=x` olur ve `foo(10)` `Symbol("foo(10)")=foo(10)` olur. Anahtar değer çiftlerinin bir listesini splatlamak için normal splatlama sözdizimini kullanın, `@info "blah" kws...`.

Otomatik olarak üretilen log verilerini geçersiz kılmak için bazı anahtarlar vardır:

  * `_module=mod`, mesajın kaynak konumundan farklı bir köken modülü belirtmek için kullanılabilir.
  * `_group=symbol`, mesaj grubunu geçersiz kılmak için kullanılabilir (bu genellikle kaynak dosyasının temel adından türetilir).
  * `_id=symbol`, otomatik olarak üretilen benzersiz mesaj tanımlayıcısını geçersiz kılmak için kullanılabilir. Bu, farklı kaynak satırlarında üretilen mesajları çok yakından ilişkilendirmek istiyorsanız yararlıdır.
  * `_file=string` ve `_line=integer`, bir log mesajının görünür kaynak konumunu geçersiz kılmak için kullanılabilir.

Ayrıca, geleneksel anlamı olan bazı anahtar değer çiftleri vardır:

  * `maxlog=integer`, mesajın en fazla `maxlog` kez görüntülenmesi gerektiği konusunda arka uca bir ipucu olarak kullanılmalıdır.
  * `exception=ex`, genellikle `@error` ile kullanılan bir log mesajıyla bir istisna taşımak için kullanılmalıdır. İlgili bir geri izleme `bt`, `exception=(ex,bt)` tuple'ı kullanılarak eklenebilir.

# Örnekler

```

julia @debug "Ayrıntılı hata ayıklama bilgisi.  Varsayılan olarak görünmez" @info  "Bilgilendirici bir mesaj" @warn  "Bir şey garipti.  Dikkat etmelisin" @error "Ölümcül olmayan bir hata oluştu"

x = 10 @info "Mesaja ekli bazı değişkenler" x a=42.0

@debug begin     sA = sum(A)     "sum(A) = :sA pahalı bir işlemdir, yalnızca `shouldlog` true döndüğünde değerlendirilir" end

for i=1:10000     @info "Varsayılan arka uç ile yalnızca (i = :i) on kez göreceksiniz"  maxlog=10     @debug "Algoritma1" i ilerleme=i/10000 end ```
