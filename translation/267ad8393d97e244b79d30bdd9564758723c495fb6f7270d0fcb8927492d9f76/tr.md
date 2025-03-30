# System Image Building

## [Building the Julia system image](@id Building-the-Julia-system-image)

Julia, `Base` modülünün içeriğini içeren bir önceden işlenmiş sistem görüntüsü ile birlikte gelir ve bu görüntü `sys.ji` olarak adlandırılır. Bu dosya, mümkün olan birçok platformda, çok daha iyi başlangıç süreleri sağlamak amacıyla `sys.{so,dll,dylib}` adlı bir paylaşılan kütüphaneye de önceden derlenmiştir. Önceden derlenmiş bir sistem görüntüsü dosyası ile birlikte gelmeyen sistemlerde, Julia'nın `DATAROOTDIR/julia/base` klasöründe bulunan kaynak dosyalarından bir tane oluşturulabilir.

Julia varsayılan olarak mevcut sistem iş parçacıklarının yarısı kadar sistem görüntüsü oluşturacaktır. Bu, [`JULIA_IMAGE_THREADS`](@ref JULIA_IMAGE_THREADS) ortam değişkeni ile kontrol edilebilir.

Bu işlem birden fazla nedenle faydalıdır. Bir kullanıcı:

  * Bir önceden derlenmiş paylaşımlı kütüphane sistem görüntüsü oluşturun ve bu görüntü, bir kütüphane ile birlikte gelmeyen bir platformda çalıştırılarak başlangıç sürelerini iyileştirin.
  * `Base`'i değiştirin, sistem görüntüsünü yeniden oluşturun ve Julia bir sonraki başlatıldığında yeni `Base`'i kullanın.
  * `userimg.jl` dosyasını dahil edin, bu dosya paketleri sistem görüntüsüne ekleyerek, başlangıç ortamına gömülü paketlere sahip bir sistem görüntüsü oluşturur.

[`PackageCompiler.jl` package](https://github.com/JuliaLang/PackageCompiler.jl) bu süreci otomatikleştirmek için kullanışlı sarmalayıcı fonksiyonlar içerir.

## [System image optimized for multiple microarchitectures](@id sysimg-multi-versioning)

Sistem görüntüsü, aynı talimat seti mimarisi (ISA) altında birden fazla CPU mikro mimarisi için aynı anda derlenebilir. Farklı ISA uzantılarından veya diğer mikro mimari özelliklerinden yararlanmak amacıyla, paylaşılan işlevlere minimum dağıtım noktası eklenerek aynı işlevin birden fazla versiyonu oluşturulabilir. En iyi performansı sunan versiyon, mevcut CPU özelliklerine dayalı olarak çalışma zamanında otomatik olarak seçilecektir.

### Specifying multiple system image targets

Bir çok mikro mimari sistem görüntüsü, sistem görüntüsü derlemesi sırasında birden fazla hedef geçilerek etkinleştirilebilir. Bu, ya [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) make seçeneği ile ya da derleme komutunu manuel olarak çalıştırırken `-C` komut satırı seçeneği ile yapılabilir. Birden fazla hedef, seçenek dizesinde `;` ile ayrılır. Her hedefin sözdizimi, bir CPU adı ve ardından `,` ile ayrılmış birden fazla özellikten oluşur. LLVM tarafından desteklenen tüm özellikler desteklenir ve bir özellik `-` ön eki ile devre dışı bırakılabilir. (`+` ön eki de kullanılabilir ve LLVM sözdizimi ile tutarlı olması için göz ardı edilir). Ayrıca, işlev klonlama davranışını kontrol etmek için birkaç özel özellik de desteklenmektedir.

!!! note
    Her hedef için `clone_all` veya `base(<n>)` belirtmek iyi bir uygulamadır, ilk hedef hariç. Bu, hangi hedeflerin tüm işlevlerin kopyalandığını ve hangi hedeflerin diğer hedeflere dayandığını açıkça belirtir. Bu yapılmazsa, varsayılan davranış her işlevi kopyalamamak ve kopyalanmayan bir işlev için yedek olarak ilk hedefin işlev tanımını kullanmaktır.


1. `clone_all`

    Varsayılan olarak, yalnızca mikro mimari özelliklerinden en çok fayda sağlayacak olan işlevler kopyalanacaktır. Ancak, bir hedef için `clone_all` belirtildiğinde, sistem görüntüsündeki **tüm** işlevler hedef için kopyalanacaktır. Tüm işlevlerin kopyalanmasını önlemek için `-clone_all` negatif biçimi kullanılabilir.
2. `taban(<n>)`

    Burada `<n>`, negatif olmayan bir sayı için bir yer tutucudur (örneğin, `base(0)`, `base(1)`). Varsayılan olarak, kısmen klonlanmış (yani `clone_all` değil) bir hedef, bir işlev klonlanmadığında varsayılan hedeften (belirtilen ilk) işlevleri kullanacaktır. Bu davranış, `base(<n>)` seçeneği ile farklı bir temel belirterek değiştirilebilir. `n`'inci hedef (0'dan başlayarak) varsayılan (`0`'ıncı) hedef yerine temel hedef olarak kullanılacaktır. Temel hedef ya `0` olmalı ya da başka bir `clone_all` hedefi olmalıdır. Temel hedef olarak bir `clone_all` olmayan hedef belirtmek bir hataya neden olacaktır.
3. `opt_size`

    Bu, hedefin işlevinin, önemli bir çalışma zamanı performans etkisi olmadığında boyut için optimize edilmesine neden olur. Bu, `-Os` GCC ve Clang seçeneğine karşılık gelir.
4. `min_size`

    Bu, hedefin boyut için optimize edilmesine neden olur ve bu da önemli bir çalışma zamanı performans etkisi yaratabilir. Bu, `-Oz` Clang seçeneğine karşılık gelir.

Örnek olarak, bu yazının yazıldığı sırada, julialang.org adresinden indirilebilen resmi `x86_64` Julia ikili dosyalarının oluşturulmasında aşağıdaki dize kullanılmaktadır:

```
generic;sandybridge,-xsaveopt,clone_all;haswell,-rdrnd,base(1)
```

Bu, üç ayrı hedefle bir sistem görüntüsü oluşturur; biri genel bir `x86_64` işlemcisi için, biri `xsaveopt`'u açıkça hariç tutan bir `sandybridge` ISA'sı ile tüm işlevleri açıkça klonlayan ve diğeri `sandybridge` sysimg sürümüne dayanan ve ayrıca `rdrnd`'yi hariç tutan `haswell` ISA'sını hedef alır. Bir Julia uygulaması oluşturulan sysimg'i yüklediğinde, ana işlemciyi eşleşen CPU yetenek bayrakları için kontrol eder ve mümkün olan en yüksek ISA seviyesini etkinleştirir. Temel seviye (`generic`) `cx16` talimatını gerektirir, bu bazı sanallaştırma yazılımlarında devre dışı bırakılmıştır ve `generic` hedefinin yüklenebilmesi için etkinleştirilmesi gerekir. Alternatif olarak, daha fazla uyumluluk için `generic,-cx16` hedefi ile bir sysimg oluşturulabilir, ancak bunun bazı kodlarda performans ve kararlılık sorunlarına neden olabileceğini unutmayın.

### Implementation overview

Bu, uygulamanın uygulanmasında yer alan farklı parçaların kısa bir özetidir. Daha fazla uygulama ayrıntısı için her bileşen için kod yorumlarına bakın.

1. Sistem görüntü derlemesi

    `src/processor*` içindeki ayrıştırma ve klonlama kararı verilmektedir. Şu anda döngülerin, simd talimatlarının veya diğer matematiksel işlemlerin (örneğin fastmath, fma, muladd) varlığına dayalı olarak fonksiyon klonlamayı destekliyoruz. Bu bilgi, gerçek klonlamayı yapan `src/llvm-multiversioning.cpp` dosyasına iletilir. Klonlama yapmanın yanı sıra, dağıtım slotlarını ekler (bunun nasıl yapıldığı için `MultiVersioning::runOnModule` içindeki yorumlara bakın), geçiş ayrıca sistem görüntüsünün doğru bir şekilde yüklenip başlatılabilmesi için meta veriler de üretir. Meta verilerin ayrıntılı bir açıklaması `src/processor.h` dosyasında mevcuttur.
2. Sistem görüntüsü yükleniyor

    Sistem görüntüsünün yüklenmesi ve başlatılması, sistem görüntüsü oluşturma sırasında kaydedilen meta verilerin ayrıştırılmasıyla `src/processor*` içinde yapılır. Ana bilgisayar özelliklerinin tespiti ve seçim kararı, ISA'ya bağlı olarak `src/processor_*.cpp` içinde yapılır. Hedef seçimi, tam CPU adı eşleşmesini, daha büyük vektör kayıt boyutunu ve daha fazla özellik sayısını tercih eder. Bu sürecin genel bir görünümü `src/processor.cpp` içindedir.
