# Working with LLVM

Bu, LLVM belgelerinin bir yerine geçmez, ancak Julia için LLVM üzerinde çalışırken kullanışlı ipuçlarının bir derlemesidir.

## Overview of Julia to LLVM Interface

Julia varsayılan olarak LLVM ile dinamik bağlantı kurar. Statik bağlantı kurmak için `USE_LLVM_SHLIB=0` ile derleyin.

Julia AST'yi LLVM IR'ye düşürmek veya doğrudan yorumlamak için kod `src/` dizinindedir.

| File                             | Description                                                        |
|:-------------------------------- |:------------------------------------------------------------------ |
| `aotcompile.cpp`                 | Compiler C-interface entry and object file emission                |
| `builtins.c`                     | Builtin functions                                                  |
| `ccall.cpp`                      | Lowering [`ccall`](@ref)                                           |
| `cgutils.cpp`                    | Lowering utilities, notably for array and tuple accesses           |
| `codegen.cpp`                    | Top-level of code generation, pass list, lowering builtins         |
| `debuginfo.cpp`                  | Tracks debug information for JIT code                              |
| `disasm.cpp`                     | Handles native object file and JIT code diassembly                 |
| `gf.c`                           | Generic functions                                                  |
| `intrinsics.cpp`                 | Lowering intrinsics                                                |
| `jitlayers.cpp`                  | JIT-specific code, ORC compilation layers/utilities                |
| `llvm-alloc-helpers.cpp`         | Julia-specific escape analysis                                     |
| `llvm-alloc-opt.cpp`             | Custom LLVM pass to demote heap allocations to the stack           |
| `llvm-cpufeatures.cpp`           | Custom LLVM pass to lower CPU-based functions (e.g. haveFMA)       |
| `llvm-demote-float16.cpp`        | Custom LLVM pass to lower 16b float ops to 32b float ops           |
| `llvm-final-gc-lowering.cpp`     | Custom LLVM pass to lower GC calls to their final form             |
| `llvm-gc-invariant-verifier.cpp` | Custom LLVM pass to verify Julia GC invariants                     |
| `llvm-julia-licm.cpp`            | Custom LLVM pass to hoist/sink Julia-specific intrinsics           |
| `llvm-late-gc-lowering.cpp`      | Custom LLVM pass to root GC-tracked values                         |
| `llvm-lower-handlers.cpp`        | Custom LLVM pass to lower try-catch blocks                         |
| `llvm-muladd.cpp`                | Custom LLVM pass for fast-match FMA                                |
| `llvm-multiversioning.cpp`       | Custom LLVM pass to generate sysimg code on multiple architectures |
| `llvm-propagate-addrspaces.cpp`  | Custom LLVM pass to canonicalize addrspaces                        |
| `llvm-ptls.cpp`                  | Custom LLVM pass to lower TLS operations                           |
| `llvm-remove-addrspaces.cpp`     | Custom LLVM pass to remove Julia addrspaces                        |
| `llvm-remove-ni.cpp`             | Custom LLVM pass to remove Julia non-integral addrspaces           |
| `llvm-simdloop.cpp`              | Custom LLVM pass for [`@simd`](@ref)                               |
| `pipeline.cpp`                   | New pass manager pipeline, pass pipeline parsing                   |
| `sys.c`                          | I/O and operating system utility functions                         |

Bazı `.cpp` dosyaları, tek bir nesneye derlenen bir grup oluşturur.

İçsel ile yerleşik arasındaki fark, yerleşik birinci sınıf bir işlevdir ve diğer Julia işlevleri gibi kullanılabilir. İçsel ise yalnızca kutulanmamış veriler üzerinde çalışabilir ve bu nedenle argümanları statik olarak türlendirilmiş olmalıdır.

### [Alias Analysis](@id LLVM-Alias-Analysis)

Julia şu anda LLVM'nin [Type Based Alias Analysis](https://llvm.org/docs/LangRef.html#tbaa-metadata) kullanıyor. Dahil etme ilişkilerini belgeleyen yorumları bulmak için `src/codegen.cpp` dosyasında `static MDNode*` ifadesini arayın.

`-O` seçeneği, LLVM'nin [Basic Alias Analysis](https://llvm.org/docs/AliasAnalysis.html#the-basic-aa-pass) özelliğini etkinleştirir.

## Building Julia with a different version of LLVM

LLVM'nin varsayılan sürümü `deps/llvm.version` dosyasında belirtilmiştir. Bunu, üst düzey dizinde `Make.user` adında bir dosya oluşturarak ve içine şu şekilde bir satır ekleyerek geçersiz kılabilirsiniz:

```
LLVM_VER = 13.0.0
```

LLVM sürüm numaralarının yanı sıra, en son geliştirme sürümüyle derlemek için `USE_BINARYBUILDER_LLVM = 0` ile birlikte `DEPS_GIT = llvm` kullanabilirsiniz.

LLVM'nin hata ayıklama sürümünü oluşturmak için `Make.user` dosyanızda ya `LLVM_DEBUG = 1` ya da `LLVM_DEBUG = Release` ayarını yapabilirsiniz. İlki, LLVM'nin tamamen optimize edilmemiş bir sürümünü oluşturacak, ikincisi ise optimize edilmiş bir sürümünü üretecektir. İhtiyaçlarınıza bağlı olarak, ikincisi yeterli olacaktır ve oldukça daha hızlıdır. `LLVM_DEBUG = Release` kullanıyorsanız, farklı geçişler için tanılama etkinleştirmek amacıyla `LLVM_ASSERTIONS = 1` ayarını da yapmalısınız. Sadece `LLVM_DEBUG = 1` bu seçeneği varsayılan olarak ifade eder.

## Passing options to LLVM

LLVM'ye seçenekler geçmek için [`JULIA_LLVM_ARGS`](@ref JULIA_LLVM_ARGS) ortam değişkenini kullanabilirsiniz. İşte `bash` sözdizimi kullanarak örnek ayarlar:

  * `export JULIA_LLVM_ARGS=-print-after-all` her geçişten sonra IR'yi döker.
  * `export JULIA_LLVM_ARGS=-debug-only=loop-vectorize` döngü vektörleştirici için LLVM `DEBUG(...)` tanılamalarını döker. "Bilinmeyen komut satırı argümanı" hakkında uyarılar alırsanız, LLVM'yi `LLVM_ASSERTIONS = 1` ile yeniden derleyin.
  * `export JULIA_LLVM_ARGS=-help` mevcut seçeneklerin bir listesini gösterir. `export JULIA_LLVM_ARGS=-help-hidden` ise daha fazlasını gösterir.
  * `export JULIA_LLVM_ARGS="-fatal-warnings -print-options"` birden fazla seçeneğin nasıl kullanılacağını gösteren bir örnektir.

### Useful `JULIA_LLVM_ARGS` parameters

  * `-print-after=PASS`: `PASS`'in herhangi bir yürütülmesinden sonra IR'yi yazdırır, bir geçiş tarafından yapılan değişiklikleri kontrol etmek için yararlıdır.
  * `-print-before=PASS`: `PASS`'in herhangi bir yürütülmesinden önce IR'yi yazdırır, bir geçişe girdi kontrol etmek için yararlıdır.
  * `-print-changed`: IR'yi değiştiren her geçişte IR'yi yazdırır, hangi geçişlerin sorunlara neden olduğunu daraltmak için yararlıdır.
  * `-print-(before|after)=MARKER-PASS`: Julia boru hattı, sorunların veya optimizasyonların nerede meydana geldiğini belirlemek için kullanılabilecek bir dizi işaretçi geçişi ile birlikte gelir. Bir işaretçi geçişi, boru hattında bir kez görünen ve IR üzerinde herhangi bir dönüşüm gerçekleştirmeyen bir geçiş olarak tanımlanır ve yalnızca print-before/print-after hedeflemek için yararlıdır. Şu anda, boru hattında aşağıdaki işaretçi geçişleri mevcuttur:

      * ÖnceOptimizasyon
      * ÖnceErkenBasitleştirme
      * Sonra Erken Basitleştirme
      * ÖnceErkenOptimizasyon
      * SonraErkenOptimizasyon
      * ÖnceDöngüOptimizasyonu
      * ÖnceLICM
      * AfterLICM
      * ÖnceDöngüBasitleştirme
      * AfterLoopSimplification
      * AfterLoopOptimization
      * ÖnceSkalarOptimizasyonu
      * SonraSkalarOptimizasyonu
      * ÖnceVektörleştirme
      * Sonraki Vektörleştirme
      * Önceki İçsel Düşürme
      * AfterIntrinsicLowering
      * ÖnceTemizlik
      * SonraTemizlik
      * SonrasıOptimizasyon
  * `-time-passes`: her geçişte harcanan zamanı yazdırır, hangi geçişlerin uzun sürdüğünü belirlemek için faydalıdır.
  * `-print-module-scope`: `-print-(before|after)` ile birlikte kullanıldığında, geçiş tarafından alınan IR birimi yerine tüm modülü alır.
  * `-debug`: LLVM boyunca birçok hata ayıklama bilgisi yazdırır
  * `-debug-only=NAME`, `NAME` ile tanımlı `DEBUG_TYPE`'a sahip dosyalardan hata ayıklama ifadelerini yazdırır, bir sorun hakkında ek bağlam elde etmek için yararlıdır.

## Debugging LLVM transformations in isolation

Bazen, LLVM'nin dönüşümlerini Julia sisteminin geri kalanından izole bir şekilde hata ayıklamak faydalı olabilir; örneğin, `julia` içinde sorunu yeniden üretmek çok uzun süreceği için veya LLVM'nin araçlarından (örneğin, bugpoint) yararlanmak istendiği için.

LLVM ile çalışmak için geliştirici araçlarını şu şekilde kurabilirsiniz:

```
make -C deps install-llvm-tools
```

Tüm sistem görüntüsü için optimize edilmemiş IR almak için, sistem görüntüsü oluşturma sürecine `--output-unopt-bc unopt.bc` seçeneğini geçin; bu, optimize edilmemiş IR'yi `unopt.bc` dosyasına çıkartacaktır. Bu dosya daha sonra LLVM araçlarına her zamanki gibi geçirilebilir. `libjulia`, LLVM araçlarına yüklenebilen bir LLVM geçiş eklentisi olarak işlev görebilir ve bu ortamda julia'ya özgü geçişlerin kullanılabilir olmasını sağlar. Ayrıca, IR üzerinde tüm Julia geçiş boru hattını çalıştıran `-julia` meta-geçişini de açığa çıkarır. Örneğin, eski geçiş yöneticisi ile bir sistem görüntüsü oluşturmak için, şöyle yapılabilir:

```

llc -o sys.o opt.bc
cc -shared -o sys.so sys.o
```

Yeni geçiş yöneticisi ile bir sistem görüntüsü oluşturmak için şunları yapabilirsiniz:

```
opt -load-pass-plugin=libjulia-codegen.so --passes='julia' -o opt.bc unopt.bc
llc -o sys.o opt.bc
cc -shared -o sys.so sys.o
```

Bu sistem görüntüsü daha sonra `julia` tarafından her zamanki gibi yüklenebilir.

Bir Julia fonksiyonu için yalnızca bir LLVM IR modülünü dökmek de mümkündür, kullanarak:

```julia
fun, T = +, Tuple{Int,Int} # Substitute your function of interest here
optimize = false
open("plus.ll", "w") do file
    println(file, InteractiveUtils._dump_function(fun, T, false, false, false, true, :att, optimize, :default, false))
end
```

Bu dosyalar, yukarıda gösterilen optimize edilmemiş sysimg IR ile aynı şekilde işlenebilir.

## Running the LLVM test suite

LLVM testlerini yerel olarak çalıştırmak için önce araçları kurmanız, julia'yı derlemeniz ve ardından testleri çalıştırmanız gerekir:

```
make -C deps install-llvm-tools
make -j julia-src-release
make -C test/llvmpasses
```

Eğer bireysel test dosyalarını doğrudan, her test dosyasının en üstündeki komutlar aracılığıyla çalıştırmak istiyorsanız, buradaki ilk adım araçları `./usr/tools/opt` dizinine kurmuş olacaktır. Ardından `%s`'yi test dosyasının adıyla manuel olarak değiştirmek isteyeceksiniz.

## Improving LLVM optimizations for Julia

LLVM kodu üretimini geliştirmek genellikle ya Julia'nın alt seviyesini LLVM'nin geçişlerine daha dost olacak şekilde değiştirmeyi ya da bir geçişi geliştirmeyi içerir.

Eğer bir geçişi geliştirmeyi planlıyorsanız, [LLVM developer policy](https://llvm.org/docs/DeveloperPolicy.html) adresini okumayı unutmayın. En iyi strateji, LLVM'nin `opt` aracını kullanarak kod örneğini, ilgi alanınızdaki geçişle birlikte izole bir şekilde inceleyebileceğiniz bir formda oluşturmaktır.

1. Create an example Julia code of interest.
2. `JULIA_LLVM_ARGS=-print-after-all` kullanarak IR'yi dökün.
3. İlgili pasın atılmasından hemen önceki noktada IR'yi seçin.
4. Hata ayıklama meta verilerini kaldırın ve TBAA meta verilerini elle düzeltin.

Son adım iş gücü yoğun. Daha iyi bir yol hakkında öneriler memnuniyetle karşılanır.

## The jlcall calling convention

Julia'nın optimize edilmemiş kod için genel bir çağrı konvansiyonu vardır, bu da aşağıdaki gibi görünmektedir:

```c
jl_value_t *any_unoptimized_call(jl_value_t *, jl_value_t **, int);
```

ilk argüman kutulu fonksiyon nesnesi, ikinci argüman yığın üzerindeki argümanlar dizisi ve üçüncü argüman argüman sayısıdır. Şimdi, basit bir düşürme gerçekleştirebilir ve argüman dizisi için bir alloca yayabiliriz. Ancak bu, çağrı noktasındaki kullanımların SSA doğasını ihlal eder ve optimizasyonları (GC kök yerleştirmesi dahil) önemli ölçüde zorlaştırır. Bunun yerine, aşağıdaki gibi yayımlıyoruz:

```llvm
call %jl_value_t *@julia.call(jl_value_t *(*)(...) @any_unoptimized_call, %jl_value_t *%arg1, %jl_value_t *%arg2)
```

Bu, optimizasyon süresince kullanımların SSA-olma durumunu korumamıza olanak tanır. GC kök yerleştirmesi daha sonra bu çağrıyı orijinal C ABI'ye düşürecektir.

## GC root placement

GC kök yerleştirmesi, LLVM geçiş boru hattında geç bir aşamada yapılır. GC kök yerleştirmesinin bu kadar geç yapılması, LLVM'nin GC kökleri gerektiren kod etrafında daha agresif optimizasyonlar yapmasına olanak tanır ve ayrıca gerekli GC köklerinin ve GC kök depolama işlemlerinin sayısını azaltmamıza yardımcı olur (çünkü LLVM GC'mizi anlamadığından, GC çerçevesine depolanan değerlerle ne yapıp ne yapamayacağını bilmez, bu nedenle temkinli bir şekilde çok az şey yapar). Bir örnek olarak, bir hata yolunu düşünün.

```julia
if some_condition()
    #= Use some variables maybe =#
    error("An error occurred")
end
```

Sürekli katlama sırasında, LLVM koşulun her zaman yanlış olduğunu keşfedebilir ve temel bloğu kaldırabilir. Ancak, GC kök düşürmesi erken yapılırsa, silinen blokta kullanılan GC kök slotları ve yalnızca hata yolunda kullanıldıkları için hayatta tutulan herhangi bir değer LLVM tarafından hayatta tutulur. GC kök düşürmesini geç yapmakla, LLVM'ye herhangi bir olağan optimizasyonunu (sürekli katlama, ölü kod ortadan kaldırma vb.) yapma izni vermiş oluruz, hangi değerlerin GC tarafından izlenip izlenmeyeceği konusunda (çok fazla) endişelenmeden.

Ancak, geç GC kök yerleştirmesi yapabilmek için a) hangi işaretçilerin GC tarafından takip edildiğini ve b) bu işaretçilerin tüm kullanımlarını tanımlayabilmemiz gerekiyor. Bu nedenle, GC yerleştirme geçişinin amacı basittir:

GC köklerinin/saklama alanlarının sayısını, her güvenli noktada, canlı GC ile izlenen herhangi bir işaretçinin (yani, bu noktadan sonra bu işaretçiyi kullanan bir yolun bulunduğu) bazı GC slotlarında bulunması koşuluna tabi olarak en aza indirin.

### Representation

Ana zorluk, programın optimizasyon işleminden geçtikten sonra GC ile izlenen işaretçileri ve bunların kullanımını tanımlamamıza olanak tanıyan bir IR temsili seçmektir. Tasarımımız bunu başarmak için üç LLVM özelliğinden yararlanmaktadır:

  * Özel adres alanları
  * Operand Paketleri
  * Tam sayılı işaretçiler

Özel adres alanları, her noktayı optimizasyonlar sırasında korunması gereken bir tamsayı ile etiketlememize olanak tanır. Derleyici, orijinal programda mevcut olmayan adres alanları arasında dönüşümler ekleyemez ve bir yükleme/depolama vb. işlemi sırasında bir işaretçinin adres alanını asla değiştirmemelidir. Bu, hangi işaretçilerin GC tarafından izlenmekte olduğunu optimizasyona dirençli bir şekilde belirtmemizi sağlar. Metadata'nın aynı amaca ulaşamayacağını unutmayın. Metadata, programın anlamsını değiştirmeden her zaman atılabilir olmalıdır. Ancak, bir GC tarafından izlenen işaretçiyi tanımlayamamak, sonuçta ortaya çıkan program davranışını dramatik bir şekilde değiştirir - muhtemelen çökmesine veya yanlış sonuçlar döndürmesine neden olur. Şu anda üç farklı adres alanı kullanıyoruz (numaraları `src/codegen_shared.cpp` dosyasında tanımlanmıştır):

  * GC İzlenen Göstergeler (şu anda 10): Bunlar, bir GC çerçevesine konulabilecek kutulu değerlere işaret eden göstergelerdir. C tarafında bir `jl_value_t*` göstergesi ile gevşek bir eşdeğerdir. Not: Bu adres alanında, bir GC slotuna kaydedilemeyecek bir gösterge bulundurmak yasaktır.
  * Türev Göstergeler (şu anda 11): Bunlar, bazı GC tarafından izlenen bir göstergeden türetilen göstergelerdir. Bu göstergelerin kullanımları, orijinal göstergenin kullanımlarını üretir. Ancak, bunlar kendileri GC tarafından bilinmek zorunda değildir. GC kök yerleştirme geçişi, bu göstergenin türetildiği GC tarafından izlenen göstergenin her zaman bulunmasını ve bunu kök göstergesi olarak kullanmasını sağlamalıdır.
  * Callee Rooted Pointers (şu anda 12): Bu, bir çağrılan köklü değerin kavramını ifade etmek için bir yardımcı adres alanıdır. Bu adres alanının tüm değerleri bir GC köküne saklanabilir OLMALIDIR (bunun gelecekte gevşetilmesi mümkün olsa da), ancak diğer işaretçilerden farklı olarak bir çağrıya geçildiğinde köklü olmaları gerekmez (tanım ile çağrı arasında başka bir güvenli nokta boyunca canlılarsa köklü olmaları gerekir).
  * İzlenen nesneden yüklenen işaretçiler (şu anda 13): Bu, kendileri yönetilen verilere işaret eden bir işaretçi içeren diziler tarafından kullanılır. Bu veri alanı dizi tarafından sahiplenilir, ancak kendisi bir GC tarafından izlenen nesne değildir. Derleyici, bu işaretçi canlı olduğu sürece, bu işaretçinin yüklendiği nesnenin canlı kalacağını garanti eder.

### Invariants

GC kökü yerleştirme geçişi, ön uç tarafından gözlemlenmesi gereken ve optimizasyon aracı tarafından korunan birkaç değişmezden yararlanır.

İlk olarak, yalnızca aşağıdaki adres alanı dönüşümleri izin verilir:

  * 0->{İzlenen,Türetilmiş,Çağrı Kökü}: İzlenmeyen bir işaretçiyi diğerlerinden herhangi birine dönüştürmek kabul edilebilir. Ancak, optimizasyonun böyle bir değeri köklendirmemek için geniş bir yetkiye sahip olduğunu unutmayın. Programın herhangi bir bölümünde, bir GC kökü gerektiren bir değerden (veya ondan türetilmişse) bir değerin adres alanında 0'da bulunması asla güvenli değildir.
  * Takip Edildi->Türetildi: Bu, iç değerler için standart çürüme yoludur. Yerleştirme geçişi, herhangi bir kullanım için temel işaretçiyi tanımlamak üzere bunları arayacaktır.
  * Tracked->CalleeRooted: Addrspace CalleeRooted, bir GC kökü gerekmiyor olduğuna dair yalnızca bir ipucu olarak hizmet eder. Ancak, Derived->CalleeRooted çürümesinin yasaklandığını unutmayın, çünkü işaretçiler genellikle bu adres alanında bile bir GC slotuna kaydedilebilir olmalıdır.

Şimdi bir kullanımın neyi oluşturduğunu düşünelim:

  * Yükler, yüklenmiş değerlerin bir adres alanında olduğu yüklerdir.
  * Bir adres alanındaki bir değerin bir konuma depolanması
  * Bir adres alanındaki bir işaretçiye depolar
  * Adres alanlarından birinde bir değerin operand olduğu çağrılar
  * jlcall ABI'sinde, argüman dizisinin bir değer içerdiği çağrılar
  * Lütfen çevirmek istediğiniz Markdown içeriğini veya metni paylaşın.

Yükleme/depolama ve basit çağrılara, İzlenen/Türetilen adres alanlarında açıkça izin veriyoruz. jlcall argüman dizilerinin elemanları her zaman İzlenen adres alanında olmalıdır (bu, geçerli `jl_value_t*` işaretçileri olmaları gerektiği için ABI tarafından gereklidir). Dönüş talimatları için de aynı şey geçerlidir (ancak yapı dönüş argümanlarının herhangi bir adres alanına sahip olmasına izin verildiğini unutmayın). CalleeRooted işaretçisinin yalnızca bir çağrıya (uygun şekilde türlendirilmiş bir operand içermesi gereken) geçirilmesi, izin verilen tek kullanımıdır.

Ayrıca, `getelementptr`'yi Tracked adres alanında yasaklıyoruz. Bunun nedeni, işlem bir noop olmadıkça, elde edilen işaretçinin bir GC slotuna geçerli bir şekilde saklanamayacak olması ve bu nedenle bu adres alanında olmamasıdır. Böyle bir işaretçi gerekiyorsa, önce addrspace Derived'a dönüştürülmelidir.

Son olarak, bu adres alanlarında `inttoptr`/`ptrtoint` talimatlarına izin vermiyoruz. Bu talimatların varlığı, bazı `i64` değerlerinin gerçekten GC tarafından izleniyor olduğu anlamına gelir. Bu sorunludur, çünkü GC ile ilgili işaretçileri tanımlama gereksinimini ihlal eder. Bu değişmezlik, LLVM 5.0'da yeni olan LLVM "bütünleşik olmayan işaretçiler" özelliği kullanılarak sağlanır. Bu, optimizasyoncunun bu işlemleri tanıtan optimizasyonlar yapmasını engeller. JIT zamanında `inttoptr` kullanarak adres alanı 0'da statik sabitler ekleyebileceğimizi ve ardından uygun adres alanına geçebileceğimizi unutmayın.

### Supporting [`ccall`](@ref)

Bir tartışmada şu ana kadar eksik kalan önemli bir yön, [`ccall`](@ref) ile ilgili olanıdır. `4d61726b646f776e2e436f64652822222c20226363616c6c2229_40726566` kullanımın yeri ve kapsamının örtüşmediği tuhaf bir özelliğe sahiptir. Bir örnek olarak düşünün:

```julia
A = randn(1024)
ccall(:foo, Cvoid, (Ptr{Float64},), A)
```

Düşürme sırasında, derleyici diziden işaretçiye bir dönüşüm ekleyecek ve bu, dizi değerine olan referansı düşürecektir. Ancak, elbette, [`ccall`](@ref) işlemini yaparken dizinin hayatta kalmasını sağlamamız gerekiyor. Bunun nasıl yapıldığını anlamak için, yukarıdaki kodun varsayımsal bir yaklaşık düşürülmesine bakalım:

```julia
return $(Expr(:foreigncall, :(:foo), Cvoid, svec(Ptr{Float64}), 0, :(:ccall), Expr(:foreigncall, :(:jl_array_ptr), Ptr{Float64}, svec(Any), 0, :(:ccall), :(A)), :(A)))
```

Son `:(A)`, son bir ek argüman listesi, kod üreteciye hangi Julia düzey değerlerinin bu [`ccall`](@ref) süresince canlı tutulması gerektiğini bildiren bir bilgidir. Bu bilgiyi alır ve IR düzeyinde bir "operand paketi" olarak temsil ederiz. Bir operand paketi esasen çağrı noktasına eklenmiş sahte bir kullanımdır. IR düzeyinde, bu şöyle görünür:

```llvm
call void inttoptr (i64 ... to void (double*)*)(double* %5) [ "jl_roots"(%jl_value_t addrspace(10)* %A) ]
```

GC kök yerleştirme geçişi, `jl_roots` operand paketini sanki normal bir operandmış gibi ele alacaktır. Ancak, son bir adım olarak, GC kökleri eklendikten sonra, talimat seçiminde kafa karışıklığını önlemek için operand paketini kaldıracaktır.

### Supporting [`pointer_from_objref`](@ref)

[`pointer_from_objref`](@ref) özel bir durumdur çünkü kullanıcının GC köklenmesi üzerinde açık kontrol almasını gerektirir. Yukarıdaki invariants'larımıza göre, bu fonksiyon yasadışıdır çünkü 10'dan 0'a bir adres alanı dönüşümü gerçekleştirir. Ancak, belirli durumlarda yararlı olabilir, bu yüzden özel bir intrinsic sağlıyoruz:

```llvm
declared %jl_value_t *julia.pointer_from_objref(%jl_value_t addrspace(10)*)
```

hangi GC kökü düşürme işleminden sonra ilgili adres alanı dönüşümüne düşürülmüştür. Ancak bu içsel işlevi kullanarak, çağıranın söz konusu değerin köklü olmasını sağlamak için tüm sorumluluğu üstlendiğini unutmayın. Ayrıca bu içsel işlev bir kullanım olarak kabul edilmez, bu nedenle GC kökü yerleştirme geçişi işlev için bir GC kökü sağlamayacaktır. Sonuç olarak, dış köklendirme, değer sistem tarafından hala izlenirken düzenlenmelidir. Yani, bu işlemin sonucunu küresel bir kök oluşturmak için kullanmaya çalışmak geçerli değildir - optimizasyon işlemi değeri zaten düşürmüş olabilir.

### Keeping values alive in the absence of uses

Belirli durumlarda, bir nesneyi canlı tutmak gerekli olabilir, bu nesnenin derleyici görünümünde bir kullanımı olmasa bile. Bu, doğrudan bir nesnenin bellek temsili üzerinde çalışan düşük seviyeli kodlar veya C kodu ile arayüz oluşturması gereken kodlar için geçerli olabilir. Bunu sağlamak için, LLVM seviyesinde aşağıdaki içsel işlevleri sunuyoruz:

```
token @llvm.julia.gc_preserve_begin(...)
void @llvm.julia.gc_preserve_end(token)
```

(`llvm.` adındaki kısım, `token` türünü kullanabilmek için gereklidir). Bu intrinlerin anlamı şu şekildedir: `gc_preserve_begin` çağrısı tarafından domine edilen, ancak buna karşılık gelen bir `gc_preserve_end` çağrısı (yani bir `gc_preserve_begin` çağrısından dönen token'ı argüman olarak alan bir çağrı) tarafından domine edilmeyen herhangi bir güvenli noktada, o `gc_preserve_begin`'e argüman olarak geçirilen değerler canlı tutulacaktır. `gc_preserve_begin`'in bu değerlerin normal bir kullanımı olarak sayıldığını unutmayın, bu nedenle standart yaşam süresi semantikleri, değerlerin koruma bölgesine girmeden önce canlı tutulmasını sağlayacaktır.
