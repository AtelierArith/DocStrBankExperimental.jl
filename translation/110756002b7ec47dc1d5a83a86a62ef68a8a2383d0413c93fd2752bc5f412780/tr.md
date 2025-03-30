# Custom LLVM Passes

Julia'nın bir dizi özel LLVM geçişi vardır. Genel olarak, bunlar Julia'nın anlamsal bütünlüğünü korumak için çalıştırılması gereken geçişler ve LLVM IR'yi optimize etmek için Julia'nın anlamsal özelliklerinden yararlanan geçişler olarak sınıflandırılabilir.

## Semantic Passes

Bu geçişler, LLVM IR'yi bir CPU'da çalıştırılabilir hale getiren koda dönüştürmek için kullanılır. Ana amaçları, kod üretimi tarafından daha basit bir IR'nin üretilmesini sağlamaktır; bu da diğer LLVM geçişlerinin yaygın desenleri optimize etmesine olanak tanır.

### CPUFeatures

  * Dosya Adı: `llvm-cpufeatures.cpp`
  * Sınıf Adı: `CPUFeaturesPass`
  * Opt Adı: `module(CPUFeatures)`

Bu geçiş, `julia.cpu.have_fma.(f32|f64)` içselini, hedef mimariye ve işlevde mevcut olan hedef özelliklere bağlı olarak ya true ya da false olarak düşürür. Bu içsel, hızlı [fused multiply-add](https://en.wikipedia.org/wiki/Multiply%E2%80%93accumulate_operation#Fused_multiply%E2%80%93add) işlemlerine bağımlı algoritmaların, bu tür talimatlara bağımlı olmayan standart algoritmalardan daha iyi olup olmadığını belirlemek için sıklıkla kullanılır.

### DemoteFloat16

  * Dosya adı: `llvm-demote-float16.cpp`
  * SınıfAdı: `DemoteFloat16Pass`
  * Opt Adı `function(DemoteFloat16)`

Bu geçiş, [float16](https://en.wikipedia.org/wiki/Half-precision_floating-point_format) işlemlerini float32 işlemleriyle değiştirir; bu, float16 işlemlerini yerel olarak desteklemeyen mimarilerde gerçekleştirilir. Bu, herhangi bir float16 işleminin etrafına `fpext` ve `fptrunc` talimatları ekleyerek yapılır. Yerel float16 işlemlerini destekleyen mimarilerde bu geçiş bir no-op'tur.

### LateGCLowering

  * Dosya adı: `llvm-late-gc-lowering.cpp`
  * Sınıf Adı: `LateLowerGCPass`
  * Opt Adı: `function(LateLowerGCFrame)`

Bu geçiş, GC güvenli noktaları arasında işaretçileri izlemek için gereken GC kökleme işinin çoğunu gerçekleştirir. Ayrıca, birkaç içsel işlevi karşılık gelen talimat çevirisine düşürür ve daha önce belirlenen tam olmayan değişmezleri ihlal etmesine izin verilir (`pointer_from_objref` burada bir `ptrtoint` talimatına düşürülür). Bu geçiş, genellikle, herhangi bir güvenli noktada canlı olan nesne sayısını en aza indirmek için veri akışı algoritması nedeniyle tüm özel Julia geçişleri arasında en fazla zamanı alır.

### FinalGCLowering

  * Dosya Adı: `llvm-final-gc-lowering.cpp`
  * Sınıf Adı: `FinalLowerGCPass`
  * Opt Name: `modül(FinalLowerGC)`

Bu geçiş, `libjulia` kütüphanesindeki işlevleri hedef alan birkaç son intrinsi son biçimlerine indirger. Bunu `LateGCLowering`'den ayırmak, diğer arka uçların (GPU derlemesi) bu intrinsikler için kendi özel indirme işlemlerini sağlamasına olanak tanır ve Julia boru hattının bu arka uçlarda da kullanılmasını sağlar.

### LowerHandlers

  * Dosya adı: `llvm-lower-handlers.cpp`
  * Sınıf Adı: `LowerExcHandlersPass`
  * Opt Adı: `function(AşağıExcHandlers)`

Bu geçiş, istisna işleme içgüdülerini, aslında istisnaları işlerken çağrılan çalışma zamanı işlevlerine yapılan çağrılara dönüştürür.

### RemoveNI

  * Dosya adı: `llvm-remove-ni.cpp`
  * Sınıf Adı: `RemoveNIPass`
  * Opt Adı: `module(RemoveNI)`

Bu geçiş, modülün veri düzeni dizesinden tam sayı olmayan adres alanlarını kaldırır. Bu, arka ucun Julia'nın özel adres alanlarını doğrudan makine koduna indirmesine olanak tanır; her işaretçi işlemini adres alanı 0'a yeniden yazmanın maliyetli bir şekilde yapılmasına gerek kalmaz.

### SIMDLoop

  * Dosya adı: `llvm-simdloop.cpp`
  * Sınıf Adı: `LowerSIMDLoopPass`
  * Opt Name: `loop(DüşükSIMD Döngüsü)`

Bu geçiş, `@simd` anotasyonunun ana sürücüsü olarak işlev görür. Kod oluşturma, bir döngünün arka dalına `!llvm.loopid` işaretleyicisini ekler; bu geçiş, başlangıçta `@simd` ile işaretlenmiş döngüleri tanımlamak için bunu kullanır. Ardından, bu geçiş, bir azaltma oluşturan bir dizi kayan nokta işlemi arar ve yeniden birleştirmeye (ve dolayısıyla vektörleştirmeye) izin vermek için `contract` ve `reassoc` hızlı matematik bayraklarını ekler. Bu geçiş, ne döngü bilgilerini ne de çıkarım doğruluğunu korur, bu nedenle Julia semantiğini beklenmedik şekillerde ihlal edebilir. Eğer döngü `ivdep` ile de anotasyonlanmışsa, o zaman geçiş döngüyü döngü taşıyan bağımlılıkları olmayan bir döngü olarak işaretler (kullanıcı anotasyonu yanlışsa veya yanlış döngüye uygulanırsa, sonuç davranışı tanımsızdır).

### LowerPTLS

  * Dosya Adı: `llvm-ptls.cpp`
  * Sınıf Adı: `LowerPTLSPass`
  * Opt Adı: `module(LowerPTLSPass)`

Bu geçiş, thread-local Julia intrinsics'lerini assembly talimatlarına indirger. Julia, çöp toplama ve çoklu iş parçacığı görev zamanlaması için thread-local depolamaya güvenir. Sistem görüntüleri ve paket görüntüleri için kod derlerken, bu geçiş, yükleme zamanında başlatılan global değişkenlerden yüklemelerle intrinsics çağrılarını değiştirir.

Eğer kod üretimi `swiftself` argümanı ve çağrı sözleşmesi ile bir fonksiyon üretiyorsa, bu geçiş `swiftself` argümanının pgcstack olduğunu varsayar ve intrinsics'i bu argümanla değiştirir. Bunu yapmak, yavaş iş parçacığı yerel depolama erişimlerine sahip mimarilerde hız artışları sağlar.

### RemoveAddrspaces

  * Dosya adı: `llvm-remove-addrspaces.cpp`
  * Sınıf Adı: `RemoveAddrspacesPass`
  * Opt Adı: `module(RemoveAddrspaces)`

Bu geçiş, bir adres alanındaki işaretçileri başka bir adres alanına yeniden adlandırır. Bu, LLVM IR'den Julia'ya özgü adres alanlarını kaldırmak için kullanılır.

### RemoveJuliaAddrspaces

  * Dosya adı: `llvm-remove-addrspaces.cpp`
  * Sınıf Adı: `RemoveJuliaAddrspacesPass`
  * Opt Adı: `module(RemoveJuliaAddrspaces)`

Bu geçiş, LLVM IR'den Julia'ya özgü adres alanlarını kaldırır. Çoğunlukla, LLVM IR'yi daha az karmaşık bir formatta görüntülemek için kullanılır. Dahili olarak, RemoveAddrspaces geçişinden türetilmiştir.

### Multiversioning

  * Dosya Adı: `llvm-multiversioning.cpp`
  * Sınıf Adı: `MultiVersioningPass`
  * Opt Name: `modül(JuliaÇokVersiyonlama)`

Bu geçiş, farklı mimarilerde çalışacak şekilde optimize edilmiş işlevler oluşturmak için bir modülde değişiklikler yapar (daha fazla ayrıntı için bkz. sysimg.md ve pkgimg.md). Uygulama açısından, işlevleri kopyalar ve bunlara, o platform için vektörleştirme ve talimat zamanlaması gibi gelişmiş özellikleri kullanmasına izin vermek için farklı hedefe özgü nitelikler uygular. Ayrıca, Julia görüntü yükleyicisinin, yükleyicinin çalıştığı mimariye dayalı olarak çağrılacak işlevin uygun sürümünü seçmesini sağlamak için bazı altyapılar oluşturur. Hedefe özgü nitelikler, derleme sırasında [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) ortam değişkeninden türetilen `julia.mv.specs` modül bayrağı ile kontrol edilir. Geçişin ayrıca, değeri 1 olan bir `julia.mv.enable` modül bayrağı sağlanarak etkinleştirilmesi gerekir.

!!! warning
    `llvmcall` kullanımı çoklu versiyonlama ile tehlikelidir. `llvmcall`, Julia API'leri tarafından genellikle sunulmayan özelliklere erişim sağlar ve bu nedenle genellikle tüm mimarilerde mevcut değildir. Çoklu versiyonlama etkinleştirildiğinde ve bir hedef mimari için kod üretimi talep edildiğinde, bu mimari `llvmcall` ifadesi tarafından gereken özelliği desteklemiyorsa, LLVM muhtemelen bir hata verecek, muhtemelen bir abort ile birlikte `LLVM ERROR: Bu operatörün sonucunu nasıl böleceğini bilmiyorum!` mesajını verecektir.


### GCInvariantVerifier

  * Dosya Adı: `llvm-gc-invariant-verifier.cpp`
  * Sınıf Adı: `GCInvariantVerifierPass`
  * Opt Adı: `module(GCInvariantVerifier)`

Bu geçiş, Julia'nın LLVM IR hakkındaki değişmezlerini doğrulamak için kullanılır. Bu, Julia'nın [non-integral address spaces](https://llvm.org/docs/LangRef.html#non-integral-pointer-type) [^nislides] içindeki `ptrtoint` varlığının olmaması ve yalnızca kutsanmış `addrspacecast` talimatlarının varlığı (İzlenen -> Türetilmiş, 0 -> İzlenen, vb.) gibi şeyleri içerir. IR üzerinde herhangi bir dönüşüm gerçekleştirmez.

[^nislides]: https://llvm.org/devmtg/2015-02/slides/chisnall-pointers-not-int.pdf

## Optimization Passes

Bu geçişler, LLVM'nin kendisinin gerçekleştirmeyeceği LLVM IR üzerinde dönüşümler yapmak için kullanılır; örneğin, hızlı matematik bayrağı yayılması, kaçış analizi ve Julia'ya özgü iç işlevler üzerindeki optimizasyonlar. Bu optimizasyonları gerçekleştirmek için Julia'nın anlamı hakkında bilgi kullanırlar.

### CombineMulAdd

  * Dosya adı: `llvm-muladd.cpp`
  * Sınıf Adı: `CombineMulAddPass`
  * Opt Name: `function(CombineMulAdd)`

Bu geçiş, bir `fmul` ile hızlı bir `fadd` kombinasyonunu optimize etmek için hizmet eder ve bunu bir sözleşme `fmul` ile hızlı bir `fadd` haline getirir. Bu daha sonra arka uç tarafından [fused multiply-add](https://en.wikipedia.org/wiki/Multiply%E2%80%93accumulate_operation#Fused_multiply%E2%80%93add) talimatına optimize edilir; bu, daha fazla [unpredictable semantics](https://simonbyrne.github.io/notes/fastmath/) maliyetiyle önemli ölçüde daha hızlı işlemler sağlayabilir.

!!! note
    Bu optimizasyon yalnızca `fmul`'ün tek bir kullanımı olduğunda gerçekleşir, bu da hızlı `fadd`'dir.


### AllocOpt

  * Dosya Adı: `llvm-alloc-opt.cpp`
  * Sınıf Adı: `AllocOptPass`
  * Opt Adı: `function(AllocOpt)`

Julia, değiştirilebilir nesneleri tahsis etmek için bir program yığını kavramına sahip değildir. Ancak, nesneleri yığında tahsis etmek GC baskısını azaltır ve GPU derlemesi için kritik öneme sahiptir. Bu nedenle, `AllocOpt`, mevcut işlevi [escape](https://en.wikipedia.org/wiki/Escape_analysis) kanıtlayabildiği nesnelerin yığın dönüşümünü gerçekleştirir. Ayrıca, asla kullanılmayan tahsisleri kaldırmak, yeni tahsis edilen nesneler için typeof çağrılarını optimize etmek ve hemen üzerine yazılan tahsilatlara yapılan atamaları kaldırmak gibi tahsisler üzerinde bir dizi başka optimizasyon gerçekleştirir. Kaçış analizi uygulaması `llvm-alloc-helpers.cpp` dosyasında bulunmaktadır. Şu anda, bu geçiş `EscapeAnalysis.jl`'den bilgi kullanmamaktadır, ancak bu gelecekte değişebilir.

### PropagateJuliaAddrspaces

  * Dosya Adı: `llvm-propagate-addrspaces.cpp`
  * Sınıf Adı: `PropagateJuliaAddrspacesPass`
  * Opt Name: `function(PropagateJuliaAddrspaces)`

Bu geçiş, işaretçiler üzerindeki işlemler aracılığıyla Julia'ya özgü adres alanlarını yaymak için kullanılır. LLVM, optimizasyonlar tarafından addrspacecast talimatlarını eklemeye veya kaldırmaya izin verilmez, bu nedenle bu geçiş, işlemleri Julia adres alanındaki eşdeğerleriyle değiştirmek suretiyle gereksiz addrspace cast'leri ortadan kaldırmak için çalışır. Julia'nın adres alanları hakkında daha fazla bilgi için (TODO llvm.md bağlantısı).

### JuliaLICM

  * Dosya Adı: `llvm-julia-licm.cpp`
  * Sınıf Adı: `JuliaLICMPass`
  * Opt Adı: `loop(JuliaLICM)`

Bu geçiş, Julia'ya özgü içsel işlevleri döngülerden çıkarmak için kullanılır. Özellikle, aşağıdaki dönüşümleri gerçekleştirir:

1. `gc_preserve_begin`'i döngülerden çıkarın ve `gc_preserve_end`'i, korunan nesnelerin döngü-değişmez olduğu durumlarda aşağıya indirin.

    1. Döngü içinde korunan nesnelerin döngü süresince korunma olasılığı yüksek olduğundan, bu dönüşüm IR'deki `gc_preserve_begin`/`gc_preserve_end` çiftlerinin sayısını azaltabilir. Bu, `LateLowerGCPass`'ın belirli nesnelerin nerede korunduğunu tanımlamasını kolaylaştırır.
2. Invariant nesneleri ile yazma engellerini yukarı kaldırın

    1. Burada bir nesnenin yalnızca iki nesil parçası olabileceğini varsayıyoruz. Bunu göz önünde bulundurarak, bir yazma engelinin aynı nesne için yalnızca bir kez çalıştırılması gerekir. Böylece, yazma engellerini, yazılan nesnenin döngü-değişmez olduğu durumlarda döngülerden çıkarabiliriz.
3. Döngülerden kaçmayan tahsisatları döngülerin dışına çıkarın.

    1. Burada kaçışın çok muhafazakar bir tanımını kullanıyoruz, bu `AllocOptPass`'ta kullanılanla aynı. Bu dönüşüm, bir tahsisin tamamen işlevden kaçtığı durumlarda bile IR'deki tahsis sayısını azaltabilir.

!!! note
    Bu geçiş, LLVM'nin [MemorySSA](https://llvm.org/docs/MemorySSA.html) ([Short Video](https://www.youtube.com/watch?v=bdxWmryoHak), [Longer Video](https://www.youtube.com/watch?v=1e5y6WDbXCQ)) ve [ScalarEvolution](https://baziotis.cs.illinois.edu/compilers/introduction-to-scalar-evolution.html) ([Newer Slides](https://llvm.org/devmtg/2018-04/slides/Absar-ScalarEvolution.pdf) [Older Slides](https://llvm.org/devmtg/2009-10/ScalarEvolutionAndLoopOptimization.pdf)) analizlerini korumak için gereklidir.

