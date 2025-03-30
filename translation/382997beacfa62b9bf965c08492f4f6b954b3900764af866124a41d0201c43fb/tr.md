```
Base.@assume_effects ayar... [ex]
```

Derleyicinin etki modellemesini geçersiz kılın. Bu makro birkaç bağlamda kullanılabilir:

1. Bir yöntem tanımından hemen önce, uygulanan yöntemin tüm etki modellemesini geçersiz kılmak için.
2. Hiçbir argümanı olmayan bir işlev gövdesinde, kapsayıcı yöntemin tüm etki modellemesini geçersiz kılmak için.
3. Bir kod bloğuna uygulandığında, uygulanan kod bloğunun yerel etki modellemesini geçersiz kılmak için.

# Örnekler

```jldoctest
julia> Base.@assume_effects :terminates_locally function fact(x)
           # kullanım 1:
           # bu :terminates_locally `fact`'in sabit katlanmasına izin verir
           res = 1
           0 ≤ x < 20 || error("kötü faktöriyel")
           while x > 1
               res *= x
               x -= 1
           end
           return res
       end
fact (generic function with 1 method)

julia> code_typed() do
           fact(12)
       end |> only
CodeInfo(
1 ─     return 479001600
) => Int64

julia> code_typed() do
           map((2,3,4)) do x
               # kullanım 2:
               # bu :terminates_locally bu anonim işlevin sabit katlanmasına izin verir
               Base.@assume_effects :terminates_locally
               res = 1
               0 ≤ x < 20 || error("kötü faktöriyel")
               while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}

julia> code_typed() do
           map((2,3,4)) do x
               res = 1
               0 ≤ x < 20 || error("kötü faktöriyel")
               # kullanım 3:
               # bu :terminates_locally notasyonu ile derleyici kirletmeyi atlar
               # `:terminates` etkisi bu `while` bloğu içinde, ebeveyn
               # anonim işlevin sabit katlanmasına izin verir
               Base.@assume_effects :terminates_locally while x > 1
                   res *= x
                   x -= 1
               end
               return res
           end
       end |> only
CodeInfo(
1 ─     return (2, 6, 24)
) => Tuple{Int64, Int64, Int64}
```

!!! uyum "Julia 1.8"
    `Base.@assume_effects` kullanmak Julia sürüm 1.8 gerektirir.


!!! uyum "Julia 1.10"
    Bir işlev gövdesi içindeki kullanım en az Julia 1.10 gerektirir.


!!! uyum "Julia 1.11"
    Kod bloğu notasyonu en az Julia 1.11 gerektirir.


!!! uyarı     Bu makronun yanlış kullanımı tanımsız davranışa (çökmeler, yanlış cevaplar veya diğer zor izlenebilir hatalar dahil) yol açar. Dikkatli kullanın ve kesinlikle gerekli olmadıkça son çare olarak kullanın. Böyle bir durumda bile, etki beyanının gücünü en aza indirmek için tüm olası adımları ATARAK almalısınız (örneğin, `:nothrow` yeterli olsaydı `:total` kullanmayın).

Genel olarak, her `ayar` değeri, derleyicinin bu davranışın gerçekten doğru olduğunu kanıtlamasını gerektirmeden, işlevin davranışı hakkında bir beyan yapar. Bu beyanlar tüm dünya yaşları için yapılır. Bu nedenle, varsayımı geçersiz kılabilecek daha sonra genişletilebilecek genel işlevlerin kullanımını sınırlamak tavsiye edilir (bu tanımsız davranışa yol açar).

Aşağıdaki `ayar`lar desteklenmektedir.

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:terminates_locally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:noub_if_noinbounds`
  * `:nortcall`
  * `:foldable`
  * `:removable`
  * `:total`

# Genişletilmiş yardım

---

## `:consistent`

`:consistent` ayarı, egal (`===`) girdiler için:

  * Sonlanma şeklinin (dönüş değeri, istisna, sonsuz döngü) her zaman aynı olacağını beyan eder.
  * Eğer yöntem dönerse, sonuçlar her zaman egal olacaktır.

!!! not
    Bu özellikle, yöntemin taze tahsis edilmiş bir değiştirilebilir nesne döndürmemesi gerektiğini ima eder. Değiştirilebilir nesnelerin birden fazla tahsisi (aynı içeriklerle bile) egal değildir.


!!! not
    `:consistent`-cy beyanı dünya yaşı açısından yapılır. Daha resmi olarak, $fᵢ$'yi dünya yaşı $i$'de $f$'nin değerlendirilmesi için yazın, bu ayar şunu gerektirir:

    $$
    ∀ i, x, y: x ≡ y → fᵢ(x) ≡ fᵢ(y)
    $$

    Ancak, iki dünya yaşı $i$, $j$ için $i ≠ j$ olduğunda, $fᵢ(x) ≢ fⱼ(y)$ olabilir.

    Bir diğer sonuç, `:consistent` işlevlerinin dönüş değerini yığın durumunun veya belirli bir dünya yaşı için sabit olmayan herhangi bir küresel durumun durumuna bağlı hale getiremeyeceğidir.


!!! not
    `:consistent`-cy, optimizasyoncunun gerçekleştirdiği tüm yasal yeniden yazımları içerir. Örneğin, kayan nokta hızlı matematik işlemleri `:consistent` olarak kabul edilmez, çünkü optimizasyoncu bunları yeniden yazabilir ve çıktı `:consistent` olmayabilir, aynı dünya yaşı için bile (örneğin, biri yorumlayıcıda çalışırken, diğeri optimize edilmiş olabilir).


!!! not
    Eğer `:consistent` işlevleri bir istisna fırlatarak sonlanırsa, o istisnanın yukarıda belirtilen egalite gereksinimini karşılaması gerekmez.


---

## `:effect_free`

`:effect_free` ayarı, yöntemin dışsal olarak anlamsal olarak görünür yan etkilerden arınmış olduğunu beyan eder. Aşağıda dışsal olarak anlamsal olarak görünür yan etkilerin eksik bir listesi bulunmaktadır:

  * Küresel bir değişkenin değerini değiştirmek.
  * Yığını değiştirmek (örneğin, bir dizi veya değiştirilebilir değer), aşağıda belirtilenler dışında
  * Yöntem tablosunu değiştirmek (örneğin, eval çağrıları aracılığıyla)
  * Dosya/Ağ vb. G/Ç
  * Görev değiştirme

Ancak, aşağıdakiler açıkça anlamsal olarak görünür değildir, hatta gözlemlenebilir olsalar bile:

  * Bellek tahsisleri (hem değiştirilebilir hem de değiştirilemez)
  * Geçen zaman
  * Çöp toplama
  * Yöntemin ömrünü aşmayan nesnelerin yığın değişiklikleri (yani, yöntemde tahsis edilen ve kaçmayan).
  * Döndürülen değer (dışsal olarak görünür, ancak bir yan etki değildir)

Buradaki kural, dışsal olarak görünür bir yan etkinin, işlev çalıştırılmadığında programın geri kalanının yürütülmesini etkileyecek herhangi bir şey olduğudur.

!!! not
    `:effect_free` beyanı, hem yöntem için hem de yöntemin yürüttüğü herhangi bir kod için yapılır. Bu beyanın tüm dünya yaşları için geçerli olması gerektiğini unutmayın ve bu beyanın kullanımını buna göre sınırlayın.


---

## `:nothrow`

`:nothrow` ayarları, bu yöntemin bir istisna fırlatmadığını (yani her zaman bir değer döndüreceğini veya asla dönmeyeceğini) beyan eder.

!!! not
    `:nothrow` ile işaretlenmiş yöntemlerin, istisna işleme kullanmalarına izin verilir, yeter ki istisna yöntemin kendisinden yeniden fırlatılmasın.


!!! not
    Bir yöntemin `MethodError` ve benzeri istisnaları yükseltme olasılığı varsa, o yöntem `:nothrow` olarak kabul edilmez. Ancak, `StackOverflowError` veya `InterruptException` gibi ortam bağımlı hataların bu etki tarafından modellenmediğini ve dolayısıyla `StackOverflowError` ile sonuçlanabilecek bir yöntemin `!:nothrow` olması gerekmediğini unutmayın (ancak genellikle `!:terminates` olması gerekir).


---

## `:terminates_globally`

`:terminates_globally` ayarları, bu yöntemin nihayetinde sonlanacağını (ya normal ya da anormal), yani sonsuz döngüye girmeyeceğini beyan eder.

!!! not
    Bu `:terminates_globally` beyanı, notasyonlu yöntemi çağıran diğer yöntemleri kapsar.


!!! not
    Derleyici, bu yöntemin nispeten *hızlı* bir şekilde sonlanacağına dair güçlü bir gösterge olarak bunu dikkate alacaktır ve (aksi takdirde yasal ise) bu yöntemi derleme zamanında çağırabilir. Yani, teknik olarak ama pratikte sonlanan bir yönteme bu ayarı eklemek kötü bir fikirdir.


---

## `:terminates_locally`

`:terminates_locally` ayarı, `:terminates_globally` gibi, ancak yalnızca notasyonlu yöntemin içindeki sözdizimsel kontrol akışına uygulanır. Bu nedenle, yöntemin bazı diğer yöntemleri çağırması durumunda sonlanmama olasılığını mümkün kılan çok daha zayıf (ve dolayısıyla daha güvenli) bir beyanıdır.

!!! not
    `:terminates_globally`, `:terminates_locally`'yi ima eder.


---

## `:notaskstate`

`:notaskstate` ayarı, yöntemin yerel görev durumunu (görev yerel depolama, RNG durumu vb.) kullanmadığını veya değiştirmediğini beyan eder ve bu nedenle görevler arasında gözlemlenebilir sonuçlar olmadan güvenle taşınabilir.

!!! not
    İstisna işlemenin uygulanması, görev nesnesinde saklanan durumu kullanır. Ancak, bu durum şu anda `:notaskstate` kapsamına alınmamaktadır ve `:nothrow` etkisi kullanılarak ayrı olarak izlenmektedir.


!!! not
    `:notaskstate` beyanı, *şu anda çalışan görev* durumunu ilgilendirir. Eğer bir `Task` nesnesine başka bir yöntemle erişim sağlanırsa ve bu, *şu anda* hangi görevin çalıştığını dikkate almazsa, `:notaskstate` etkisi kirletilmek zorunda değildir. Bu, söz konusu görev nesnesinin şu anda çalışan görevle `===` olması durumunda bile geçerlidir.


!!! not
    Görev durumuna erişim genellikle diğer etkilerin kirletilmesine de yol açar, örneğin `:effect_free` (eğer görev durumu değiştirilirse) veya `:consistent` (eğer görev durumu sonuç hesaplamasında kullanılırsa). Özellikle, `:notaskstate` olmayan, ancak `:effect_free` ve `:consistent` olan kod hala ölü koddan çıkarılabilir ve dolayısıyla `:total`'a terfi edilebilir.


---

## `:inaccessiblememonly`

`:inaccessiblememonly` ayarı, yöntemin dışarıdan erişilebilir değiştirilebilir belleği erişmediğini veya değiştirmediğini beyan eder. Bu, yöntemin, döndürüldükten önce diğer yöntemler veya üst düzey yürütme tarafından erişilemeyen yeni tahsis edilmiş nesnelerin değiştirilebilir belleğini erişmesine veya değiştirmesine izin verir, ancak herhangi bir değiştirilebilir küresel durumu veya argümanları tarafından işaret edilen değiştirilebilir belleği erişemez veya değiştiremez.

!!! not
    Aşağıda, bu varsayımı geçersiz kılacak örneklerin eksik bir listesi bulunmaktadır:

      * bir küresel referans veya değiştirilebilir bir küresel değişkeni erişmek için `getglobal` çağrısı
      * bir küresel atama veya sabit olmayan bir küresel değişkene atama yapmak için `setglobal!` çağrısı
      * bir küresel değiştirilebilir değişkenin bir alanını değiştiren `setfield!` çağrısı


!!! not
    Bu `:inaccessiblememonly` beyanı, notasyonlu yöntemi çağıran diğer yöntemleri kapsar.


---

## `:noub`

`:noub` ayarı, yöntemin herhangi bir tanımsız davranış gerçekleştirmeyeceğini beyan eder (herhangi bir girdi için). Tanımsız davranışın teknik olarak yöntemin diğer etki beyanlarını (örneğin `:consistent` veya `:effect_free`) ihlal etmesine neden olabileceğini unutmayın, ancak bunu modellemiyoruz ve tanımsız davranışın yokluğunu varsayıyoruz.

---

## `:nortcall`

`:nortcall` ayarı, yöntemin `Core.Compiler.return_type` çağrısı yapmadığını ve bu yöntemin çağırabileceği diğer yöntemlerin de `Core.Compiler.return_type` çağrısı yapmadığını beyan eder.

!!! not
    Kesin olmak gerekirse, bu beyan, `Core.Compiler.return_type` çağrısının çalışma zamanında yapılmadığı durumlarda kullanılabilir; yani, `Core.Compiler.return_type`'ın sonucu derleme zamanında tam olarak biliniyorsa ve çağrı optimizasyoncu tarafından ortadan kaldırılıyorsa. Ancak, `Core.Compiler.return_type`'ın sonucunun derleme zamanında katlanıp katlanmadığı, derleyicinin uygulamasına bağlı olduğundan, bu yöntemin `Core.Compiler.return_type`'ı herhangi bir biçimde kullandığı durumlarda bunu beyan etmek genellikle risklidir.


---

## `:foldable`

Bu ayar, derleyicinin bir çağrıyı derleme zamanında sabit katlama garantisi vermesi için gereken etki seti için uygun bir kısayoldur. Şu anda aşağıdaki `ayar`lara eşdeğerdir:

  * `:consistent`
  * `:effect_free`
  * `:terminates_globally`
  * `:noub`
  * `:nortcall`

!!! not
    Bu liste özellikle `:nothrow`'u içermez. Derleyici hala sabit yayılma denemesi yapacak ve derleme zamanında herhangi bir fırlatılan hatayı not edecektir. Ancak, `:consistent`-cy gereksinimleri gereği, böyle bir notasyonlu çağrı, aynı argüman değerleri verildiğinde tutarlı bir şekilde fırlatmalıdır.


!!! not
    İşlev içinde açık bir `@inbounds` notasyonu da sabit katlamayı devre dışı bırakır ve `:foldable` ile geçersiz kılınamaz.


---

## `:removable`

Bu ayar, derleyicinin kullanılmayan bir çağrının sonucunu derleme zamanında silme garantisi vermesi için gereken etki seti için uygun bir kısayoldur. Şu anda aşağıdaki `ayar`lara eşdeğerdir:

  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`

---

## `:total`

Bu `ayar`, mümkün olan en yüksek etki setidir. Şu anda aşağıdaki diğer `ayar`ları ima eder:

  * `:consistent`
  * `:effect_free`
  * `:nothrow`
  * `:terminates_globally`
  * `:notaskstate`
  * `:inaccessiblememonly`
  * `:noub`
  * `:nortcall`

!!! uyarı     `:total`, çok güçlü bir beyan olup, gelecekteki Julia sürümlerinde ek anlamlar kazanabilir (örneğin, ek etkiler eklenip `:total` tanımına dahil edilebilir). Sonuç olarak, dikkatli kullanılmalıdır. Mümkün olduğunda, belirli bir uygulama için gereken en az etki beyanı setini kullanmayı tercih edin. Bir dizi işlev için büyük sayıda etki geçersiz kılmaları uygulandığında, `:total` kullanımı yerine özel bir makro önerilir.

---

## Olumsuz etkiler

Etki adları, daha önceki bir meta etkiden etkiyi kaldırmak için `!` ile ön eklenebilir. Örneğin, `:total !:nothrow`, çağrının genel olarak toplam olduğunu, ancak yine de fırlatabileceğini belirtir.
