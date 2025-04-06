# [Proper maintenance and care of multi-threading locks](@id Proper-maintenance-and-care-of-multi-threading-locks)

Aşağıdaki stratejiler, kodun dead-lock'suz olmasını sağlamak için kullanılmaktadır (genellikle 4. Coffman koşulunu: dairesel beklemeyi ele alarak).

> 1. structure code such that only one lock will need to be acquired at a time
> 2. her zaman aşağıdaki tabloda verilen sırayla paylaşılan kilitleri aynı sırayla alın
> 3. sınırsız özyineleme gerektirecek yapıları kullanmaktan kaçının


## Locks

Aşağıda sistemde mevcut olan tüm kilitler ve bunları kullanma mekanizmaları, potansiyel ölü kilitlenmeleri önlemek için (burada Ostrich algoritması yoktur) bulunmaktadır:

Aşağıdakiler kesinlikle yaprak kilitleridir (seviye 1) ve başka bir kilit edinmeye çalışmamalıdır:

>   * safepoint
>
>     > Not edin ki bu kilit, `JL_LOCK` ve `JL_UNLOCK` tarafından örtük olarak edinilir. Seviye 1 kilitler için bunu önlemek amacıyla `_NOGC` varyantlarını kullanın.
>     >
>     > Bu kilidi tutarken, kodun herhangi bir tahsisat yapmaması veya herhangi bir güvenli noktaya ulaşmaması gerekir. Tahsisat yaparken, GC'yi etkinleştirirken/devre dışı bırakırken, istisna çerçevelerine girerken/geri yüklerken ve kilit alırken/serbest bırakırken güvenli noktaların olduğunu unutmayın.
>   * paylaşılan_harita
>   * sonlandırıcılar
>   * sayfa tahsisi
>   * gc*perm*lock
>   * flisp
>   * jl*in*stackwalk (Win32)
>   * ResourcePool<?>::mutex
>   * RLST_mutex
>   * llvm*basamak*mutex
>   * jl*kilitli*akış::mutex
>   * debuginfo_asyncsafe
>   * çıkarım*zamana*mutex
>   * ExecutionEngine::SessionLock
>
>     > flisp kendisi zaten thread güvenliğidir, bu kilit yalnızca `jl_ast_context_list_t` havuzunu korur, ayrıca ResourcePool<?>::mutexes yalnızca ilişkili kaynak havuzunu korur.


Aşağıda bir yaprak kilidi (seviye 2) bulunmaktadır ve yalnızca dahili olarak seviye 1 kilitleri (güvenli nokta) alır:

>   * global*roots*lock
>   * Modül->kilit
>   * JLDebuginfoPlugin::PluginMutex
>   * yeni*çıkarılan*mutex


Aşağıda yalnızca dahili olarak seviye 1 veya seviye 2 kilitleri alabilen seviye 3 bir kilit bulunmaktadır:

>   * Yöntem->yazma kilidi
>   * typecache


Aşağıda yalnızca seviye 1, 2 veya 3 kilitleri almak için geri dönebilme yeteneğine sahip seviye 4 bir kilit bulunmaktadır:

>   * MethodTable->yazma kilidi


Bu noktadan yukarıda bir kilit tutarken hiçbir Julia kodu çağrılmamalıdır.

orc::ThreadSafeContext (TSCtx) kilitleri, kilitleme hiyerarşisinde özel bir yere sahiptir. LLVM'nin küresel, çok iş parçacıklı olmayan durumunu korumak için kullanılırlar, ancak bunlardan keyfi sayıda olabilir. Varsayılan olarak, bu kilitlerin tümü, hiyerarşinin geri kalanıyla karşılaştırma amacıyla seviye 5 kilitleri olarak kabul edilebilir. Bir TSCtx edinmek yalnızca JIT'in TSCtx havuzundan yapılmalıdır ve o TSCtx üzerindeki tüm kilitler, havuza geri döndürülmeden önce serbest bırakılmalıdır. Birden fazla TSCtx kilidinin aynı anda edinilmesi gerekiyorsa (özyinelemeli derleme nedeniyle), kilitler, TSCtx'lerin havuzdan ödünç alındığı sıraya göre edinilmelidir.

Aşağıdaki seviye 5 kilittir

>   * JuliaOJIT::EmissionMutex


Aşağıdakiler, yalnızca daha düşük seviyelerde kilitler almak için yinelemeli olarak çalışabilen seviye 6 bir kilittir:

>   * kod üreteci
>   * jl*modüller*mutex


Aşağıdaki neredeyse kök kilidi (seviye son-1) anlamına gelir, yani onu edinmeye çalışırken yalnızca kök kilidi tutulabilir:

>   * typeinf
>
>     > bu belki de en karmaşık olanlardan biri, çünkü tür çıkarımı birçok noktadan çağrılabilir.
>     >
>     > şu anda kilit, birbirlerini özyinelemeli olarak çağırdıkları için kod oluşturma kilidi ile birleştirilmiştir.


Aşağıdaki kilit, IO işlemlerini senkronize eder. Yukarıda listelenen diğer kilitlerden herhangi birini tutarken herhangi bir I/O (örneğin, uyarı mesajları veya hata ayıklama bilgileri yazdırmak) yapmanın, kötü ve zor bulunabilen ölümlere yol açabileceğini unutmayın. ÇOK DİKKATLİ OLUN!

>   * iolock
>   * Bireysel ThreadSynchronizers kilitleri
>
>     > bu, iolock'u serbest bıraktıktan sonra devam edebilir veya onsuz edinilebilir, ancak iolock'u tutarken asla edinmeye çalışmamaya dikkat edin.
>   * Libdl.TembelKütüphane kilidi


Aşağıdaki kök kilit, onu almaya çalışırken başka bir kilidin tutulamayacağı anlamına gelir:

>   * üst seviye
>
>     > bu, yeni bir tür oluşturmak veya yeni bir yöntem tanımlamak gibi üst düzey bir eylem gerçekleştirilmeye çalışılırken tutulmalıdır: sahnelenmiş bir işlev içinde bu kilidi elde etmeye çalışmak bir kilitlenme durumuna neden olacaktır!
>     >
>     > ek olarak, *herhangi* bir kodun rastgele bir üst düzey ifade ile güvenli bir şekilde paralel çalışıp çalışamayacağı belirsizdir, bu nedenle tüm iş parçacıklarının önce bir güvenli noktaya ulaşması gerekebilir.


## Broken Locks

Aşağıdaki kilitler bozulmuştur:

  * üst seviye

    > şu anda mevcut değil
    >
    > düzelt: oluşturun
  * Modül->kilit

    > Bu, sıralı olarak edinildiğinden emin olamayacağı için deadlock'lara karşı savunmasızdır. Bazı işlemler (örneğin `import_module`) bir kilit eksik.
    >
    > düzelt: `jl_modules_mutex` ile değiştir?
  * loading.jl: `require` ve `register_root_module`

    > Bu dosyada potansiyel olarak birçok sorun var.
    >
    > düzelt: kilitlere ihtiyaç var

## Shared Global Data Structures

Bu veri yapıları, paylaşılan değişken küresel durumu nedeniyle kilitlere ihtiyaç duyar. Bu, yukarıdaki kilit öncelik listesinin tersidir. Bu liste, basitlikleri nedeniyle seviye 1 yaprak kaynaklarını içermez.

MethodTable değişiklikleri (def, cache) : MethodTable->yazma kilidi

Tip bildirimleri: üst düzey kilit

Uygulama türü: typecache kilidi

Küresel değişken tabloları : Modül->kilit

Modül serileştirici : üst düzey kilit

JIT ve tür çıkarımı: kod oluşturma kilidi

MethodInstance/CodeInstance güncellemeleri : Method->yazma kilidi, kod oluşturma kilidi

>   * Bunlar inşaatta belirlenir ve değiştirilemez:
>
>       * specTürleri
>       * sparam_vals
>       * def
>       * sahip


>   * Bunlar `jl_type_infer` tarafından belirlenir (kod oluşturma kilidi tutulurken):
>
>       * önbellek
>       * rettype
>       * çıkarılan


```
    * valid ages
```

>   * `inInference` bayrağı:
>
>       * `jl_type_infer` çalışırken tekrarına hızlıca girmeyi önlemek için optimizasyon
>       * gerçek durum (`çıkarılan`, ardından `fptr` ayarı) kod üretim kilidi ile korunmaktadır


>   * Fonksiyon işaretçileri:
>
>       * bu geçişler bir kez, `NULL`'dan bir değere, kod oluşturma kilidi tutulurken gerçekleşir
>   * Kod üreteci önbelleği ( `functionObjectsDecls` içeriği):
>
>       * bunlar birden fazla kez geçiş yapabilir, ancak yalnızca kod üretim kilidi tutulduğunda
>       * eski sürümünü kullanmak geçerlidir veya bunun yeni sürümleri için engel oluşturmak, bu nedenle yarışlar zararsızdır, yeter ki kod, yöntem örneğindeki diğer verilere (örneğin `rettype`) atıfta bulunmamaya dikkat etsin ve bunun koordine olduğunu varsaymasın, aksi takdirde kod oluşturma kilidini de tutmalıdır.


LLVMContext : kod oluşturma kilidi

Yöntem : Yöntem->yazma kilidi

  * kökler dizisi (serileştirici ve kod üreteci)
  * çağır / uzmanlıklar / tfunc değişiklikleri
