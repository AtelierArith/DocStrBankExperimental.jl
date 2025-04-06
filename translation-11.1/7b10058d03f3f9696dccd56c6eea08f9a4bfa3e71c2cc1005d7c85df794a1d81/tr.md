# Static analyzer annotations for GC correctness in C code

## Running the analysis

Analizör eklentisi, analizi yönlendiren, julia ile birlikte gelir. Kaynak kodu `src/clangsa` içinde bulunabilir. Bunu çalıştırmak, clang bağımlılığının derlenmesini gerektirir. Uygun bir clang sürümünü derlemek için Make.user dosyanızda `BUILD_LLVM_CLANG` değişkenini ayarlayın. Ayrıca, `USE_BINARYBUILDER_LLVM` seçeneklerini kullanarak önceden derlenmiş ikili dosyaları da kullanmak isteyebilirsiniz.

Alternatif olarak (veya bunlar yeterli değilse), deneyin

```sh
make -C src install-analysis-deps
```

Julia'nın üst düzey dizininden.

Sonrasında, kaynak ağaç üzerinde analizi çalıştırmak, `make -C src analyzegc` komutunu çalıştırmak kadar basittir.

## General Overview

Julia'nın GC'si hassas olduğu için, herhangi bir değer için doğru kökleme bilgilerini koruması gerekir; bu değer, GC'nin herhangi bir zamanda gerçekleşebileceği bir yerde referans alınabilir. Bu yerler `safepoint` olarak bilinir ve fonksiyonun yerel bağlamında, bu tanımı, bir safepoint'e geri dönebilme ihtimali olan herhangi bir fonksiyon çağrısını kapsayacak şekilde genişletiyoruz.

Oluşturulan kodda, bu otomatik olarak GC kök yerleştirme geçişi tarafından halledilir (LLVM kodlama geliştirici belgelerindeki GC kökleri bölümüne bakın). Ancak, C kodunda, çalışma zamanına herhangi bir GC kökünü manuel olarak bildirmemiz gerekir. Bu, aşağıdaki makrolar kullanılarak yapılır:

```
// The value assigned to any slot passed as an argument to these
// is rooted for the duration of this GC frame.
JL_GC_PUSH{1,...,6}(args...)
// The values assigned into the size `n` array `rts` are rooted
// for the duration of this GC frame.
JL_GC_PUSHARGS(rts, n)
// Pop a GC frame
JL_GC_POP
```

Bu makrolar gerektiği yerlerde kullanılmazsa veya yanlış kullanılırsa, sonuç sessiz bellek bozulmasıdır. Bu nedenle, tüm uygulanabilir kodda doğru bir şekilde yerleştirilmeleri çok önemlidir.

Bu nedenle, bu makroların doğru bir şekilde kullanılmasını sağlamak için statik analiz (özellikle clang statik analizörü) kullanıyoruz. Bu belgenin geri kalanı, bu statik analizin bir özetini verir ve işlerin düzgün çalışması için julia kod tabanında gereken desteği açıklar.

## GC Invariants

İki basit değişmezlik doğruluğu vardır:

  * Tüm `GC_PUSH` çağrılarının uygun bir `GC_POP` ile takip edilmesi gerekir (pratikte bunu fonksiyon seviyesinde zorunlu kılıyoruz)
  * Eğer bir değer daha önce herhangi bir güvenli noktada köklenmemişse, daha sonra artık referans alınmayabilir.

Elbette, detaylarda şeytan gizlidir. Özellikle yukarıdaki koşullardan ikincisini yerine getirmek için, şunları bilmemiz gerekiyor:

  * Hangi çağrılar güvenli noktalardır ve hangileri değildir
  * Hangi değerlerin belirli bir güvenli noktada köklendiği ve hangilerinin köklenmediği
  * Bir değer ne zaman referans alınır

İkinci nokta için özellikle, çalışma zamanında hangi bellek konumlarının kök olarak kabul edileceğini bilmemiz gerekiyor (yani, bu konumlara atanan değerler köklenmiştir). Bu, `GC_PUSH` makrolarından birine geçirilerek açıkça kök olarak belirlenen konumları, küresel olarak köklenmiş konumları ve değerleri, ayrıca bu konumlardan birine özyinelemeli olarak ulaşılabilen herhangi bir konumu içerir.

## Static Analysis Algorithm

Fikirin kendisi çok basit, ancak uygulama oldukça daha karmaşık (özellikle C ve C++'ın birçok özel durumu ve incelikleri nedeniyle). Özünde, köklenen tüm konumları, köklenebilir tüm değerleri ve herhangi bir ifadenin (atamalar, tahsisler vb.) köklenebilir değerlerin köklenme durumunu nasıl etkilediğini takip ediyoruz. Sonra, herhangi bir güvenli noktada, "sembolik GC" gerçekleştiriyoruz ve belirtilen konumda köklenmemiş olan değerleri zehirli hale getiriyoruz. Bu değerler daha sonra referans alındığında, bir hata bildiriyoruz.

Clang statik analizörü, durumların bir grafiğini oluşturarak ve bu grafiği hata kaynakları için keşfederek çalışır. Bu grafikteki birkaç düğüm, analizör tarafından (örneğin kontrol akışı için) oluşturulurken, yukarıdaki tanımlar bu grafiği kendi durumumuzla zenginleştirir.

Statik analizör, prosedürler arasıdır ve işlev sınırları boyunca kontrol akışını analiz edebilir. Ancak, statik analizör tam olarak özyinelemeli değildir ve hangi çağrıların inceleneceği konusunda sezgisel kararlar alır (ek olarak bazı çağrılar çeviri birimi arasında olup analizöre görünmez). Bizim durumumuzda, doğruluk tanımımız toplam bilgi gerektirir. Bu nedenle, analiz için gereken bilgileri içeren tüm işlev çağrılarının prototiplerini not etmemiz gerekir, bu bilgi aksi takdirde prosedürler arası statik analiz ile mevcut olsa bile.

Neyse ki, bu ara yüzler arası analizi kullanarak, belirli bir işlev üzerinde koyduğumuz notların, söz konusu işlevin uygulanması göz önüne alındığında gerçekten doğru olduğunu garanti edebiliriz.

## The analyzer annotations

Bu anotasyonlar src/support/analyzer_annotations.h dosyasında bulunur. Sadece analizör kullanıldığında aktiftirler ve ya hiçbir şeye (prototip anotasyonları için) ya da hiçbir işlem yapmayan ifadelere (fonksiyon benzeri anotasyonlar için) genişlerler.

### `JL_NOTSAFEPOINT`

Bu muhtemelen en yaygın notlamadır ve GC güvenli noktasına ulaşma olasılığı olmayan herhangi bir işlevde yer almalıdır. Genel olarak, böyle bir işlevin yalnızca aritmetik, bellek erişimleri ve ya `JL_NOTSAFEPOINT` ile notlanmış ya da güvenli nokta olmadığı bilinen işlevleri (örneğin, analizörde sabit kodlanmış olan C standart kütüphanesindeki işlevler) çağırması güvenlidir.

Bu niteliğe sahip herhangi bir işleve yapılan çağrılar arasında değerlerin köksüz tutulması geçerlidir:

Kullanım Örneği:

```c
void jl_get_one() JL_NOTSAFEPOINT {
  return 1;
}

jl_value_t *example() {
  jl_value_t *val = jl_alloc_whatever();
  // This is valid, even though `val` is unrooted, because
  // jl_get_one is not a safepoint
  jl_get_one();
  return val;
}
```

### `JL_MAYBE_UNROOTED`/`JL_ROOTS_TEMPORARILY`

`JL_MAYBE_UNROOTED` bir işlevin argümanı olarak belirtildiğinde, bu argümanın köklü olmasa bile geçilebileceğini gösterir. Olağan koşullar altında, julia ABI, çağıranların değerleri çağrılanlara geçirmeden önce köklü hale getirmelerini garanti eder. Ancak, bazı işlevler bu ABI'yi takip etmez ve köklü olmasalar bile değerlere geçişine izin verir. Ancak, bu durumun, söz konusu argümanın korunacağı anlamına gelmediğini unutmayın. `ROOTS_TEMPORARILY` notasyonu, değerin geçildiğinde köksüz olabileceği kadar, çağrılan tarafından herhangi bir iç güvenli nokta boyunca da korunacağına dair daha güçlü bir garanti sağlar.

`JL_NOTSAFEPOINT` temelde `JL_MAYBE_UNROOTED`/`JL_ROOTS_TEMPORARILY` anlamına gelir, çünkü bir argümanın köklülüğü, işlevin hiç güvenli nokta içermemesi durumunda önemsizdir.

Bir ek nokta, bu anotasyonların hem çağıran hem de çağrılan taraf için geçerli olduğudur. Çağıran tarafta, genellikle julia ABI fonksiyonları için gereken köklülük kısıtlamalarını kaldırırlar. Çağrılan tarafta ise, bu argümanların dolaylı olarak köklü olarak değerlendirilmesini engelleyen ters bir etkiye sahiptirler.

Eğer bu anotasyonlardan biri fonksiyona genel olarak uygulanırsa, bu fonksiyonun tüm argümanlarına uygulanır. Bu genellikle yalnızca varargs fonksiyonları için gerekli olmalıdır.

Kullanım örneği:

```c
JL_DLLEXPORT void JL_NORETURN jl_throw(jl_value_t *e JL_MAYBE_UNROOTED);
jl_value_t *jl_alloc_error();

void example() {
  // The return value of the allocation is unrooted. This would normally
  // be an error, but is allowed because of the above annotation.
  jl_throw(jl_alloc_error());
}
```

### `JL_PROPAGATES_ROOT`

Bu açıklama, başka bir nesne içinde saklanan bir köklenebilir nesneyi döndüren erişim işlevlerinde yaygın olarak bulunur. Bir işlev argümanına eklendiğinde, analizöre o argümanın kökünün, işlev tarafından döndürülen değer için de geçerli olduğunu belirtir.

Kullanım Örneği:

```c
jl_value_t *jl_svecref(jl_svec_t *t JL_PROPAGATES_ROOT, size_t i) JL_NOTSAFEPOINT;

size_t example(jl_svec_t *svec) {
  jl_value_t *val = jl_svecref(svec, 1)
  // This is valid, because, as annotated by the PROPAGATES_ROOT annotation,
  // jl_svecref propagates the rooted-ness from `svec` to `val`
  jl_gc_safepoint();
  return jl_unbox_long(val);
}
```

### `JL_ROOTING_ARGUMENT`/`JL_ROOTED_ARGUMENT`

Bu, esasen `JL_PROPAGATES_ROOT`'un atama karşılığıdır. Zaten köklü olan bir değerin bir alanına bir değer atandığında, atanan değer, atandığı değerin kökünü miras alacaktır.

Kullanım Örneği:

```c
void jl_svecset(void *t JL_ROOTING_ARGUMENT, size_t i, void *x JL_ROOTED_ARGUMENT) JL_NOTSAFEPOINT


size_t example(jl_svec_t *svec) {
  jl_value_t *val = jl_box_long(10000);
  jl_svecset(svec, val);
  // This is valid, because the annotations imply that the
  // jl_svecset propagates the rooted-ness from `svec` to `val`
  jl_gc_safepoint();
  return jl_unbox_long(val);
}
```

### `JL_GC_DISABLED`

Bu notasyon, bu işlevin yalnızca GC çalışma zamanı devre dışı bırakıldığında çağrıldığını ima eder. Bu tür işlevler en çok başlangıçta ve GC kodunun kendisinde karşılaşılır. Bu notasyonun çalışma zamanı etkinleştirme/devre dışı bırakma çağrılarına karşı kontrol edildiğini unutmayın, bu nedenle clang yalan söylediğinizi bilecektir. GC gerçekten devre dışı bırakılmadıysa, belirli bir işlevin işlenmesini devre dışı bırakmanın iyi bir yolu değildir (bunu yapmak zorundaysanız `ifdef __clang_analyzer__` kullanın).

Kullanım örneği:

```c
void jl_do_magic() JL_GC_DISABLED {
  // Wildly allocate here with no regard for roots
}

void example() {
  int en = jl_gc_enable(0);
  jl_do_magic();
  jl_gc_enable(en);
}
```

### `JL_REQUIRE_ROOTED_SLOT`

Bu anotasyon, çağıranın köklü bir slot geçmesini gerektirir (yani, bu slot'a atanan değerler köklü olacaktır).

Kullanım örneği:

```c
void jl_do_processing(jl_value_t **slot JL_REQUIRE_ROOTED_SLOT) {
  *slot = jl_box_long(1);
  // Ok, only, because the slot was annotated as rooting
  jl_gc_safepoint();
}

void example() {
  jl_value_t *slot = NULL;
  JL_GC_PUSH1(&slot);
  jl_do_processing(&slot);
  JL_GC_POP();
}
```

### `JL_GLOBALLY_ROOTED`

Bu anotasyon, belirli bir değerin her zaman küresel olarak köklü olduğunu ima eder. Bu, küresel değişken bildirimlerine uygulanabilir; bu durumda, bu değişkenlerin değerine (veya bir dizi için bildirimse değerlerine) uygulanır veya fonksiyonlara uygulanabilir; bu durumda, bu tür fonksiyonların döndürdüğü değere uygulanır (örneğin, her zaman bazı özel, küresel olarak köklü bir değer döndüren fonksiyonlar için).

Kullanım örneği:

```
extern JL_DLLEXPORT jl_datatype_t *jl_any_type JL_GLOBALLY_ROOTED;
jl_ast_context_t *jl_ast_ctx(fl_context_t *fl) JL_GLOBALLY_ROOTED;
```

### `JL_ALWAYS_LEAFTYPE`

Bu anotasyon esasen `JL_GLOBALLY_ROOTED` ile eşdeğerdir, ancak yalnızca bu değerlerin bir leaftype olma özelliği nedeniyle küresel olarak köklü olması durumunda kullanılmalıdır. Leaftype'ların köklenmesi biraz karmaşıktır. Genellikle, ilgili `TypeName`'in `cache` alanı aracılığıyla köklenir, bu alan da içeren modül tarafından köklenir (yani, içeren modül sağlam olduğu sürece köklüdürler) ve genellikle leaftype'ların kullanıldıkları yerlerde köklü olduğunu varsayabiliriz, ancak bu özelliği gelecekte daha da geliştirebiliriz, bu nedenle ayrı anotasyon, küresel olarak köklü olma nedenini ayırmaya yardımcı olur.

Analizör ayrıca leaftype-ness için kontrolleri otomatik olarak tespit eder ve bu yollar üzerindeki eksik GC kökleri hakkında şikayet etmez.

```
JL_DLLEXPORT jl_value_t *jl_apply_array_type(jl_value_t *type, size_t dim) JL_ALWAYS_LEAFTYPE;
```

### `JL_GC_PROMISE_ROOTED`

Bu, işlev benzeri bir anotasyondur. Bu anotasyona geçirilen herhangi bir değer, mevcut işlevin kapsamı için köklü olarak kabul edilecektir. Analizör yetersizliği veya karmaşık durumlar için bir kaçış kapısı olarak tasarlanmıştır. Ancak, analizörü geliştirmek yerine, nadiren kullanılmalıdır.

```
void example() {
  jl_value_t *val = jl_alloc_something();
  if (some_condition) {
    // We happen to know for complicated external reasons
    // that val is rooted under these conditions
    JL_GC_PROMISE_ROOTED(val);
  }
}
```

## Completeness of analysis

Analizör yalnızca yerel bilgilere bakar. Özellikle, yukarıdaki `PROPAGATES_ROOT` durumunda, bu tür belleğin yalnızca görebildiği şekillerde değiştirildiğini varsayar, çağrılan işlevlerde (analizinde dikkate almayı seçmediği sürece) ve eşzamanlı çalışan iş parçacıklarında değil. Bu nedenle, bazı sorunlu durumları atlayabilir, ancak pratikte böyle eşzamanlı değişiklikler oldukça nadirdir. Analizörü daha fazla böyle durumu ele alacak şekilde geliştirmek, gelecekteki çalışmalar için ilginç bir konu olabilir.
