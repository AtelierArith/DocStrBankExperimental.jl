# Eval of Julia code

Julia Dilinin kodu nasıl çalıştırdığını öğrenmenin en zor kısımlarından biri, bir kod bloğunu yürütmek için tüm parçaların nasıl bir araya geldiğini öğrenmektir.

Her bir kod parçası genellikle, potansiyel olarak tanıdık olmayan isimlerle birçok adımda bir yolculuk yapar, bunlar arasında (herhangi bir sırayla): flisp, AST, C++, LLVM, `eval`, `typeinf`, `macroexpand`, sysimg (veya sistem görüntüsü), bootstrapping, derleme, ayrıştırma, yürütme, JIT, yorumlama, kutulama, kutudan çıkarma, içsel fonksiyon ve ilkel fonksiyon bulunur; bunların hepsi istenen sonuca (umarım) dönüşmeden önce.

!!! sidebar "Definitions"
      * REPL

        REPL, Read-Eval-Print Loop'un kısaltmasıdır. Kısaca, komut satırı ortamına verdiğimiz isimdir.
      * AST

        Soyut Sözdizim Ağaçları AST, kod yapısının dijital temsilidir. Bu biçimde kod, anlamı için token'lara ayrılmıştır, böylece manipülasyon ve yürütme için daha uygun hale gelir.


![Derleyici akışının diyagramı](./img/compiler_diagram.png)

## Julia Execution

Tüm sürecin 10,000 fitlik görünümü aşağıdaki gibidir:

1. Kullanıcı `julia` başlatır.
2. `cli/loader_exe.c` dosyasındaki `main()` C fonksiyonu çağrılır. Bu fonksiyon, komut satırı argümanlarını işler, `jl_options` yapısını doldurur ve `ARGS` değişkenini ayarlar. Ardından Julia'yı başlatır (şu çağrıyı yaparak: [`julia_init` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c)), bu da daha önce derlenmiş [sysimg](@ref dev-sysimg) dosyasını yükleyebilir. Son olarak, kontrolü Julia'ya devretmek için [`Base._start()`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) çağrısını yapar.
3. `_start()` kontrolü devraldığında, sonraki komut dizisi verilen komut satırı argümanlarına bağlıdır. Örneğin, bir dosya adı sağlandıysa, o dosyayı çalıştırmaya devam edecektir. Aksi takdirde, etkileşimli bir REPL başlatacaktır.
4. Kullanıcının REPL ile etkileşimi hakkında detayları atlayarak, programın çalıştırmak istediği bir kod bloğuna ulaştığını söyleyelim.
5. Eğer çalıştırılacak kod bloğu bir dosyada ise, [`jl_load(char *filename)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) dosyayı yüklemek için çağrılır ve [parse](@ref dev-parsing) ile yüklenir. Her kod parçası daha sonra `eval` ile çalıştırılması için geçirilir.
6. Her bir kod parçası (veya AST), sonuçlara dönüştürmek için [`eval()`](@ref)'ya iletilir.
7. [`eval()`](@ref) her bir kod parçasını çalıştırmaya çalışır [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c).
8. `jl_toplevel_eval_flex()` kodun "toplevel" bir eylem olup olmadığını (örneğin `using` veya `module` gibi) belirler; bu, bir fonksiyonun içinde geçersiz olur. Eğer öyleyse, kodu toplevel yorumlayıcısına iletir.
9. `jl_toplevel_eval_flex()` ardından [expands](@ref dev-macro-expansion) makroları ortadan kaldırmak ve AST'yi daha basit bir şekilde çalıştırmak için "aşağı indirmek" amacıyla kullanılan kod.
10. `jl_toplevel_eval_flex()` daha sonra AST'yi JIT derleyip derlemeyeceğine veya doğrudan yorumlayacağına karar vermek için bazı basit sezgiler kullanır.
11. Çalışmanın büyük kısmı kodu yorumlamak için [`eval` in `interpreter.c`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c) tarafından yönetilmektedir.
12. Eğer bunun yerine kod derlenirse, işin büyük kısmı `codegen.cpp` tarafından halledilir. Bir Julia fonksiyonu, belirli bir argüman türü seti ile ilk kez çağrıldığında, [type inference](@ref dev-type-inference) o fonksiyon üzerinde çalıştırılacaktır. Bu bilgi, daha hızlı kod üretmek için [codegen](@ref dev-codegen) adımında kullanılır.
13. Sonunda, kullanıcı REPL'i kapatır veya programın sonuna ulaşılır ve `_start()` metodu döner.
14. Çıkmadan hemen önce, `main()` [`jl_atexit_hook(exit_code)`](https://github.com/JuliaLang/julia/blob/master/src/init.c) çağrısını yapar. Bu, Julia içinde [`atexit()`](@ref) ile kayıtlı olan herhangi bir fonksiyonu çağıran `Base._atexit()`'i çağırır. Ardından [`jl_gc_run_all_finalizers()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) çağrısını yapar. Son olarak, tüm `libuv` handle'larını nazikçe temizler ve bunların boşalmasını ve kapanmasını bekler.

## [Parsing](@id dev-parsing)

Julia ayrıştırıcısı, femtolisp'te yazılmış küçük bir lisp programıdır; kaynak kodu, Julia içinde [src/flisp](https://github.com/JuliaLang/julia/tree/master/src/flisp) içinde dağıtılmaktadır.

Arayüz işlevleri esasen [`jlfrontend.scm`](https://github.com/JuliaLang/julia/blob/master/src/jlfrontend.scm) içinde tanımlanmıştır. [`ast.c`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) içindeki kod, bu geçişi Julia tarafında yönetmektedir.

Bu aşamada ilgili diğer dosyalar [`julia-parser.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm), Julia kodunu tokenleştiren ve bir AST'ye dönüştüren, ve [`julia-syntax.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-syntax.scm), karmaşık AST temsillerini daha basit, "aşağıya indirilmiş" AST temsillerine dönüştüren dosyalardır; bu temsiller analiz ve yürütme için daha uygundur.

Eğer Julia'yı tamamen yeniden inşa etmeden ayrıştırıcıyı test etmek istiyorsanız, ön yüzü kendi başına aşağıdaki gibi çalıştırabilirsiniz:

```
$ cd src
$ flisp/flisp
> (load "jlfrontend.scm")
> (jl-parse-file "<filename>")
```

## [Macro Expansion](@id dev-macro-expansion)

[`eval()`](@ref) bir makro ile karşılaştığında, ifadenin değerlendirilmeden önce o AST düğümünü genişletir. Makro genişletme, `4d61726b646f776e2e436f64652822222c20226576616c28292229_40726566` (Julia'da) ile `jl_macroexpand()` (flisp'te yazılmış) parser fonksiyonu ve Julia makrosu (başka ne ile yazılabilir ki - Julia) aracılığıyla `fl_invoke_julia_macro()` ile elden ele geçişi içerir ve geri döner.

Tipik olarak, makro genişletme, [`Meta.lower()`](@ref)/`jl_expand()` çağrısı sırasında birinci adım olarak çağrılır, ancak doğrudan [`macroexpand()`](@ref)/`jl_macroexpand()` çağrısıyla da tetiklenebilir.

## [Type Inference](@id dev-type-inference)

Tip çıkarımı, Julia'da [`typeinf()` in `compiler/typeinfer.jl`](https://github.com/JuliaLang/julia/blob/master/base/compiler/typeinfer.jl) ile uygulanır. Tip çıkarımı, bir Julia fonksiyonunu inceleme ve her bir değişkeninin türleri için sınırlar belirleme sürecidir; ayrıca fonksiyonun dönüş değerinin türü için de sınırlar belirler. Bu, bilinen değiştirilemez değerlerin kutusunun açılması ve alan ofsetleri ile fonksiyon işaretçileri gibi çeşitli çalışma zamanı işlemlerinin derleme zamanı yükseltilmesi gibi birçok gelecekteki optimizasyonu mümkün kılar. Tip çıkarımı, sabit yayılımı ve iç içe alma gibi diğer adımları da içerebilir.

!!! sidebar "More Definitions"
      * JIT

        Just-In-Time Derleme İhtiyaç duyulduğunda bellek içine yerel makine kodu üreten süreçtir.
      * LLVM

        Düşük Seviye Sanal Makine (bir derleyici) Julia JIT derleyicisi, libLLVM adlı bir program/kütüphanedir. Julia'daki kod üretimi, hem bir Julia AST'sini alıp LLVM talimatlarına dönüştürme sürecini hem de LLVM'nin bunu optimize edip yerel montaj talimatlarına dönüştürme sürecini ifade eder.
      * C++

        LLVM'nin uygulandığı programlama dili, bu da demektir ki kod üretimi de bu dilde uygulanmıştır. Julia'nın geri kalan kütüphanesi ise C dilinde uygulanmıştır, kısmen daha küçük özellik setinin onu bir çapraz dil arayüzü katmanı olarak daha kullanılabilir hale getirmesi nedeniyle.
      * kutusu

        Bu terim, bir değeri alıp, çöp toplayıcı (gc) tarafından izlenen ve nesnenin türü ile etiketlenmiş verinin etrafında bir sarmalayıcı tahsis etme sürecini tanımlamak için kullanılır.
      * açmak

        Bir değeri kutulamanın tersidir. Bu işlem, o verinin türü derleme zamanında (tip çıkarımı yoluyla) tamamen bilindiğinde verilerin daha verimli bir şekilde işlenmesini sağlar.
      * genel işlev

        Birden fazla "metot" içeren ve argüman türü imzasına dayalı dinamik dağıtım için seçilen bir Julia fonksiyonu
      * anonim fonksiyon veya "metot"

        Bir isim ve tür dağıtım yetenekleri olmayan bir Julia fonksiyonu
      * ilkel fonksiyon

        C'de uygulanmış bir işlev, Julia'da "method" adıyla bir adlandırılmış işlev olarak sunulmuştur (ancak, anonim bir işleve benzer şekilde, genel işlev dağıtım yetenekleri olmadan).
      * içsel işlev

        Julia'da bir işlev olarak ortaya konmuş düşük seviyeli bir işlem. Bu sahte işlevler, doğrudan başka bir şekilde ifade edilemeyen, ham bitler üzerinde toplama ve işaret uzatma gibi işlemleri uygular. Doğrudan bitler üzerinde çalıştıkları için, bir işleve derlenmeleri ve değer üzerindeki tür bilgilerini yeniden atamak için `Core.Intrinsics.box(T, ...)` çağrısıyla çevrelenmeleri gerekir.


## [JIT Code Generation](@id dev-codegen)

Codegen, bir Julia AST'sini yerel makine koduna dönüştürme sürecidir.

JIT ortamı, [`jl_init_codegen` in `codegen.cpp`](https://github.com/JuliaLang/julia/blob/master/src/codegen.cpp) ile erken bir çağrı ile başlatılır.

Talep üzerine, bir Julia yöntemi `emit_function(jl_method_instance_t*)` fonksiyonu tarafından yerel bir işleve dönüştürülür. (Not: MCJIT kullanıldığında (LLVM v3.4+), her işlev yeni bir modüle JIT edilmelidir.) Bu fonksiyon, tüm işlev yayımlanana kadar `emit_expr()` fonksiyonunu özyinelemeli olarak çağırır.

Bu dosyanın geri kalan kısmı, belirli kod desenlerinin çeşitli manuel optimizasyonlarına ayrılmıştır. Örneğin, `emit_known_call()` birçok ilkel fonksiyonu (tanımlı olan [`builtins.c`](https://github.com/JuliaLang/julia/blob/master/src/builtins.c)) argüman türlerinin çeşitli kombinasyonları için inline yapmayı bilir.

Kod oluşturmanın diğer kısımları çeşitli yardımcı dosyalar tarafından yönetilmektedir:

  * [`debuginfo.cpp`](https://github.com/JuliaLang/julia/blob/master/src/debuginfo.cpp)

    JIT fonksiyonları için geri izleme işlemlerini yönetir
  * [`ccall.cpp`](https://github.com/JuliaLang/julia/blob/master/src/ccall.cpp)

    `abi_*.cpp` dosyaları ile birlikte ccall ve llvmcall FFI'yi yönetir.
  * [`intrinsics.cpp`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp)

    Çeşitli düşük seviyeli içsel işlevlerin yayılımını yönetir

!!! sidebar "Bootstrapping"
    Yeni bir sistem görüntüsü oluşturma sürecine "bootstrapping" denir.

    Bu kelimenin etimolojisi "kendini çizmelerinle yukarı çekmek" ifadesinden gelmektedir ve çok sınırlı bir işlev ve tanım setinden başlayarak tam özellikli bir ortam yaratma fikrini ifade etmektedir.


## [System Image](@id dev-sysimg)

Sistem görüntüsü, bir dizi Julia dosyasının önceden derlenmiş bir arşividir. Julia ile dağıtılan `sys.ji` dosyası, [`sysimg.jl`](https://github.com/JuliaLang/julia/blob/master/base/sysimg.jl) dosyasını çalıştırarak oluşturulan bir sistem görüntüsüdür ve sonuçta elde edilen ortamı (Türler, Fonksiyonlar, Modüller ve tanımlı tüm diğer değerler dahil) bir dosyaya serileştirir. Bu nedenle, `Main`, `Core` ve `Base` modüllerinin (ve başlatma işleminin sonunda ortamda bulunan diğer her şeyin) dondurulmuş bir versiyonunu içerir. Bu serileştirici/serileştirici çözümleyici, [`jl_save_system_image`/`jl_restore_system_image` in `staticdata.c`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) tarafından uygulanmaktadır.

Eğer bir sysimg dosyası yoksa (`jl_options.image_file == NULL`), bu aynı zamanda komut satırında `--build` seçeneğinin verildiğini de gösterir, bu nedenle nihai sonuç yeni bir sysimg dosyası olmalıdır. Julia başlatılırken, minimal `Core` ve `Main` modülleri oluşturulur. Ardından, mevcut dizinden `boot.jl` adlı bir dosya değerlendirilir. Julia daha sonra komut satırı argümanı olarak verilen herhangi bir dosyayı değerlendirir ve sona ulaşana kadar devam eder. Son olarak, elde edilen ortamı gelecekteki bir Julia çalışması için başlangıç noktası olarak kullanılmak üzere bir "sysimg" dosyasına kaydeder.
