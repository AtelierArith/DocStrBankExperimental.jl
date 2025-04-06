# High-level Overview of the Native-Code Generation Process

## Representation of Pointers

Kod bir nesne dosyasına yayımlandığında, işaretçiler yer değiştirmeler olarak yayımlanacaktır. Serileştirme sonrası kod, bu sabitlerden birine işaret eden herhangi bir nesnenin yeniden oluşturulmasını ve doğru çalışma zamanı işaretçisini içermesini sağlayacaktır.

Aksi takdirde, bunlar sabit sabitler olarak yayımlanacaktır.

Bu nesnelerden birini yaymak için `literal_pointer_val` çağrısını yapın. Bu, Julia değerini ve LLVM globalini izlemeyi sağlayacak, bunların hem mevcut çalışma zamanı için hem de serileştirmeden sonra geçerli olmasını sağlayacaktır.

Nesne dosyasına yayıldığında, bu global değişkenler büyük bir `gvals` tablosunda referanslar olarak saklanır. Bu, ayrıştırıcının bunlara indeksle referans vermesine ve onları geri yüklemek için Global Ofset Tablosu (GOT) benzeri özel bir manuel mekanizma uygulamasına olanak tanır.

Fonksiyon işaretçileri benzer şekilde işlenir. Büyük bir `fvals` tablosunda değerler olarak saklanırlar. Global değişkenler gibi, bu durum serileştiricinin bunlara indeksle referans vermesine olanak tanır.

`extern` fonksiyonlarının, isimler aracılığıyla, bağlayıcıdaki olağan sembol çözümleme mekanizması ile ayrı olarak ele alındığını unutmayın.

Not edin ki `ccall` fonksiyonları da ayrı bir şekilde, manuel GOT ve Prosedür Bağlantı Tablosu (PLT) aracılığıyla işlenir.

## Representation of Intermediate Values

Değerler, bir `jl_cgval_t` yapısında dolaşımda. Bu, bir R-değeri temsil eder ve onu bir yere atamak veya geçirmek için gerekli bilgileri içerir.

Onlar genellikle `mark_julia_type` (anlık değerler için) ve `mark_julia_slot` (değerlere işaretçiler için) yardımcı yapıcılarından biri aracılığıyla oluşturulurlar.

`convert_julia_type` fonksiyonu, iki tür arasında dönüşüm yapabilir. `cgval.typ`'i `typ` olarak ayarlanan bir R-değeri döndürür. İstenilen temsile nesneyi dönüştürmek için gerektiğinde yığın kutuları oluşturur, yığın kopyaları ayırır ve temsili değiştirmek için etiketli birleşimleri hesaplar.

Buna karşılık `update_julia_type`, `cgval.typ`'i yalnızca sıfır maliyetle (yani herhangi bir kod yaymadan) yapılabiliyorsa `typ` olarak değiştirecektir.

## Union representation

İçsel birleştirilmiş türler, etiketli tür temsili aracılığıyla yığın üzerinde tahsis edilebilir.

Etiketli birleşimleri işleyebilmesi gereken ilkel rutinler şunlardır:

  * mark-type
  * yerel-yükle
  * store-local
  * isa
  * is
  * emit_typeof
  * emit_sizeof
  * kutulu
  * açmak
  * özel cc-ret

Her şeyin, bu ilkelere dayanarak birleşim ayırma uygulamak için çıkarımda işlenebilir olması gerekir.

Tagged-union'un temsili `< void* union, byte selector >` çiftidir. Seçici, `byte & 0x7f` olarak sabit boyutludur ve ilk 126 isbitini birleştirir. İçindeki isbit nesnelerinin tür birliğine derinlik öncelikli bir sayım kaydeder. Sıfır indeksi, `union*`'un aslında etiketli bir yığın tahsisli `jl_value_t*` olduğunu ve etiketli bir birim olarak değil, normal bir kutulu nesne olarak ele alınması gerektiğini gösterir.

Seçicinin yüksek biti (`byte & 0x80`), `void*`'ın gerçekten bir yığın tahsisli (`jl_value_t*`) kutu olup olmadığını belirlemek için test edilebilir, böylece bir kutunun yeniden tahsis edilmesi maliyetinden kaçınılırken, düşük bitlere dayalı olarak birliğin bölünmesini verimli bir şekilde ele alma yeteneği korunur.

`byte & 0x7f` tür için kesin bir test olduğu garanti edilmiştir, eğer değer bir etiketle temsil edilebiliyorsa - asla `byte = 0x80` olarak işaretlenmeyecektir. `isa` test edilirken tür-etiketini de test etmek gerekli değildir.

`union*` bellek bölgesi *herhangi* bir boyutta tahsis edilebilir. Tek kısıtlama, `selector` tarafından şu anda belirtilen verileri içerecek kadar büyük olmasıdır. İlgili Union türü alanına göre orada saklanabilecek tüm türlerin birleşimini içerecek kadar büyük olmayabilir. Kopyalama yaparken uygun dikkat gösterin.

## Specialized Calling Convention Signature Representation

Bir `jl_returninfo_t` nesnesi, herhangi bir çağrılabilirin çağrı konvansiyonu ayrıntılarını tanımlar.

Eğer bir metodun argümanlarından veya dönüş türünden herhangi biri kutusuz olarak temsil edilebiliyorsa ve metod varargs değilse, `specTypes` ve `rettype` alanlarına dayalı olarak optimize edilmiş bir çağrı sözleşmesi imzası verilecektir.

Genel ilkeler şunlardır:

  * Temel türler int/yüzer kayıtlarında geçer.
  * Vektör kayıtlarında VecElement türlerinin demetleri geçilir.
  * Yapılar yığın üzerinde geçer.
  * Dönüş değerleri, bir gizli sret argümanı aracılığıyla döndürülecekleri bir boyut kesim noktasında, argümanlarla benzer şekilde işlenir.

Bu, `get_specsig_function` ve `deserves_sret` tarafından uygulanan toplam mantıktır.

Ayrıca, eğer dönüş tipi bir birleşimse, bir çift değer (bir işaretçi ve bir etiket) olarak döndürülebilir. Eğer birleşim değerleri yığın üzerinde tahsis edilebiliyorsa, bunları depolamak için yeterli alan da gizli bir ilk argüman olarak geçilecektir. Döndürülen işaretçinin bu alana, bir kutulu nesneye veya hatta başka bir sabit belleğe işaret edip etmeyeceği, çağrılan fonksiyona bağlıdır.
