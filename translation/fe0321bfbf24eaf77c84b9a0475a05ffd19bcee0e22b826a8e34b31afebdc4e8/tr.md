```@eval
io = IOBuffer()
release = isempty(VERSION.prerelease)
v = "$(VERSION.major).$(VERSION.minor)"
!release && (v = v*"-$(first(VERSION.prerelease))")
print(io, """
    # Julia $(v) Documentation

    Welcome to the documentation for Julia $(v).

    """)
if !release
    print(io,"""
        !!! warning "Work in progress!"
            This documentation is for an unreleased, in-development, version of Julia.
        """)
end
import Markdown
Markdown.parse(String(take!(io)))
```

Lütfen son sürümden bu yana nelerin değiştiğini görmek için [release notes](NEWS.md) dosyasını okuyun.

```@eval
release = isempty(VERSION.prerelease)
file = release ? "julia-$(VERSION).pdf" :
       "julia-$(VERSION.major).$(VERSION.minor).$(VERSION.patch)-$(first(VERSION.prerelease)).pdf"
url = "https://raw.githubusercontent.com/JuliaLang/docs.julialang.org/assets/$(file)"
import Markdown
Markdown.parse("""
!!! note
    The documentation is also available in PDF format: [$file]($url).
""")
```

## [Important Links](@id man-important-links)

Aşağıda, Julia programlama dilini öğrenirken ve kullanırken faydalı olacak bağlantıların kapsamlı olmayan bir listesi bulunmaktadır.

  * [Julia Homepage](https://julialang.org)
  * [Download Julia](https://julialang.org/downloads/)
  * [Discussion forum](https://discourse.julialang.org)
  * [Julia YouTube](https://www.youtube.com/user/JuliaLanguage)
  * [Find Julia Packages](https://julialang.org/packages/)
  * [Learning Resources](https://julialang.org/learning/)
  * [Read and write blogs on Julia](https://forem.julialang.org)

## [Introduction](@id man-introduction)

Bilimsel hesaplama, geleneksel olarak en yüksek performansı gerektirmiştir, ancak alan uzmanları günlük işlerinde genellikle daha yavaş dinamik dillere geçmiştir. Bu uygulamalar için dinamik dilleri tercih etmenin birçok iyi nedeni olduğuna inanıyoruz ve bu dillerin kullanımının azalmasını beklemiyoruz. Neyse ki, modern dil tasarımı ve derleyici teknikleri, performans ticaretini büyük ölçüde ortadan kaldırmayı ve prototipleme için yeterince verimli ve performans yoğun uygulamaları dağıtmak için yeterince verimli tek bir ortam sağlamayı mümkün kılmaktadır. Julia programlama dili bu rolü üstlenmektedir: bilimsel ve sayısal hesaplama için uygun, esnek bir dinamik dildir ve geleneksel statik olarak tiplenmiş dillerle karşılaştırılabilir performansa sahiptir.

Çünkü Julia'nın derleyicisi, Python veya R gibi diller için kullanılan yorumlayıcılardan farklıdır, Julia'nın performansının başlangıçta sezgisel olmadığını görebilirsiniz. Bir şeyin yavaş olduğunu bulursanız, başka bir şey denemeden önce [Performance Tips](@ref man-performance-tips) bölümünü okumayı şiddetle tavsiye ederiz. Julia'nın nasıl çalıştığını anladığınızda, C kadar hızlı olan kodlar yazmak kolaydır.

## [Julia Compared to Other Languages](@id man-julia-compared-other-languages)

Julia, isteğe bağlı tip verme, çoklu dispatch ve iyi performans özelliklerine sahiptir; bu, tip çıkarımı ve [just-in-time (JIT) compilation](https://en.wikipedia.org/wiki/Just-in-time_compilation) (ve [optional ahead-of-time compilation](https://github.com/JuliaLang/PackageCompiler.jl)) kullanılarak gerçekleştirilmiştir; bu, [LLVM](https://en.wikipedia.org/wiki/Low_Level_Virtual_Machine) ile uygulanmıştır. Çoklu paradigma destekler; imperatif, fonksiyonel ve nesne yönelimli programlamanın özelliklerini birleştirir. Julia, R, MATLAB ve Python gibi dillerle aynı şekilde yüksek seviyeli sayısal hesaplama için kolaylık ve ifade gücü sağlar, ancak genel programlamayı da destekler. Bunu başarmak için, Julia matematiksel programlama dillerinin soyundan gelir, ancak popüler dinamik dillerden de çok şey alır; bunlar arasında [Lisp](https://en.wikipedia.org/wiki/Lisp_(programming_language)), [Perl](https://en.wikipedia.org/wiki/Perl_(programming_language)), [Python](https://en.wikipedia.org/wiki/Python_(programming_language)), [Lua](https://en.wikipedia.org/wiki/Lua_(programming_language)) ve [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language)) bulunmaktadır.

Julia'nın tipik dinamik dillerden en önemli ayrılıkları şunlardır:

  * Temel dil çok az kısıtlama getirir; Julia Temeli ve standart kütüphane, tamsayı aritmetiği gibi temel işlemler de dahil olmak üzere, kendisiyle yazılmıştır.
  * Nesne oluşturmak ve tanımlamak için zengin bir tür dili, ayrıca isteğe bağlı olarak tür bildirimleri yapmak için de kullanılabilir.
  * Fonksiyon davranışını birçok argüman türü kombinasyonu üzerinden tanımlama yeteneği [multiple dispatch](https://en.wikipedia.org/wiki/Multiple_dispatch)
  * Farklı argüman türleri için verimli, özel kodun otomatik olarak üretilmesi
  * İyi performans, C gibi statik olarak derlenmiş dillerinkiyle yaklaşmaktadır.

Dinamik diller bazen "tipi olmayan" olarak anılsa da, kesinlikle öyle değillerdir. Her nesne, ister ilkel ister kullanıcı tanımlı olsun, bir tipe sahiptir. Ancak, çoğu dinamik dilde tip bildirimlerinin olmaması, derleyiciye değerlerin tipleri hakkında talimat verilemeyeceği ve genellikle tipler hakkında açıkça konuşulamayacağı anlamına gelir. Öte yandan, statik dillerde, birinin derleyici için tipleri – genellikle zorunlu olarak – not etmesi gerekse de, tipler yalnızca derleme zamanında var olur ve çalışma zamanında manipüle edilemez veya ifade edilemez. Julia'da, tipler kendileri çalışma zamanı nesneleridir ve derleyiciye bilgi iletmek için de kullanılabilir.

### [What Makes Julia, Julia?](@id man-what-makes-julia)

Rastgele programcıların türleri veya çoklu dağıtımı açıkça kullanması gerekmese de, bunlar Julia'nın temel birleştirici özellikleridir: fonksiyonlar, argüman türlerinin farklı kombinasyonları üzerinde tanımlanır ve en spesifik eşleşen tanıma yönlendirilerek uygulanır. Bu model, matematiksel programlama için iyi bir uyum sağlar; burada ilk argümanın geleneksel nesne yönelimli dağıtımda olduğu gibi bir işlemi "sahiplenmesi" doğal değildir. Operatörler, özel notasyona sahip fonksiyonlardır – toplama işlemini yeni kullanıcı tanımlı veri türlerine genişletmek için, `+` fonksiyonu için yeni yöntemler tanımlarsınız. Mevcut kod, yeni veri türlerine sorunsuz bir şekilde uygulanır.

Kısmen çalışma zamanı tür çıkarımı (isteğe bağlı tür açıklamaları ile desteklenmiş) ve kısmen de projenin başlangıcından itibaren performansa güçlü bir odaklanma nedeniyle, Julia'nın hesaplama verimliliği diğer dinamik dillerin verimliliğini aşmakta ve hatta statik derlenmiş dillerin verimliliği ile rekabet etmektedir. Büyük ölçekli sayısal problemler için hız her zaman kritik olmuştur, olmaya devam etmektedir ve muhtemelen her zaman öyle olacaktır: işlenen veri miktarı son on yıllarda Moore Yasası ile kolayca paralel bir şekilde ilerlemiştir.

### [Advantages of Julia](@id man-advantages-of-julia)

Julia, kullanım kolaylığı, güç ve verimliliği tek bir dilde eşsiz bir şekilde bir araya getirmeyi hedefliyor. Yukarıdakilere ek olarak, Julia'nın benzer sistemlere göre bazı avantajları şunlardır:

  * Ücretsiz ve açık kaynak ([MIT licensed](https://github.com/JuliaLang/julia/blob/master/LICENSE.md))
  * Kullanıcı tanımlı türler, yerleşik türler kadar hızlı ve kompakt.
  * Kodun performansı için vektörleştirmeye gerek yok; vektörleştirilmemiş kod hızlıdır.
  * Paralelizm ve dağıtık hesaplama için tasarlandı
  * Hafif "yeşil" iş parçacığı ([coroutines](https://en.wikipedia.org/wiki/Coroutine))
  * Göze çarpmayan ama güçlü bir tür sistemi
  * Sayısal ve diğer türler için şık ve genişletilebilir dönüşümler ve terfiler
  * Verimli destek [Unicode](https://en.wikipedia.org/wiki/Unicode) için, ancak bununla sınırlı olmamak üzere [UTF-8](https://en.wikipedia.org/wiki/UTF-8)
  * C fonksiyonlarını doğrudan çağırın (sarmalayıcılar veya özel API'ler gerekmez)
  * Diğer süreçleri yönetmek için güçlü bir kabuk benzeri yetenekler
  * Lisp benzeri makrolar ve diğer metaprogramlama olanakları
