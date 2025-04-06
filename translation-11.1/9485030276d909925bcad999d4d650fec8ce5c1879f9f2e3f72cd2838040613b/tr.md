# Embedding Julia

[Calling C and Fortran Code](@ref) içinde gördüğümüz gibi, Julia'nın C'de yazılmış fonksiyonları çağırmak için basit ve etkili bir yolu vardır. Ancak, tersine ihtiyaç duyulan durumlar da vardır: C kodundan Julia fonksiyonlarını çağırmak. Bu, Julia kodunu daha büyük bir C/C++ projesine entegre etmek için kullanılabilir; her şeyi C/C++'da yeniden yazma ihtiyacı olmadan. Julia, bunu mümkün kılmak için bir C API'sine sahiptir. Neredeyse tüm programlama dilleri, C fonksiyonlarını çağırmanın bir yoluna sahiptir, bu nedenle Julia C API'si, daha fazla dil köprüsü inşa etmek için de kullanılabilir (örneğin, Julia'yı Python, Rust veya C#'dan çağırmak). Rust ve C++ doğrudan C gömme API'sini kullanabilse de, her ikisi de bununla yardımcı olan paketlere sahiptir; C++ için [Jluna](https://github.com/Clemapfel/jluna) faydalıdır.

## High-Level Embedding

**Not**: Bu bölüm, Unix benzeri işletim sistemlerinde C içinde Julia kodunu gömmeyi kapsamaktadır. Bunu Windows'ta yapmak için, lütfen bunun ardından gelen bölüme bakın, [High-Level Embedding on Windows with Visual Studio](@ref).

Basit bir C programıyla başlıyoruz, bu program Julia'yı başlatır ve bazı Julia kodlarını çağırır:

```c
#include <julia.h>
JULIA_DEFINE_FAST_TLS // only define this once, in an executable (not in a shared library) if you want fast code.

int main(int argc, char *argv[])
{
    /* required: setup the Julia context */
    jl_init();

    /* run Julia commands */
    jl_eval_string("print(sqrt(2.0))");

    /* strongly recommended: notify Julia that the
         program is about to terminate. this allows
         Julia time to cleanup pending write requests
         and run all finalizers
    */
    jl_atexit_hook(0);
    return 0;
}
```

Bu programı oluşturmak için, Julia başlık dosyasının yolunu dahil etme yoluna eklemeli ve `libjulia` ile bağlantı kurmalısınız. Örneğin, Julia `$JULIA_DIR`'ye yüklendiğinde, yukarıdaki test programı `test.c`'yi `gcc` kullanarak derleyebilirsiniz:

```
gcc -o test -fPIC -I$JULIA_DIR/include/julia -L$JULIA_DIR/lib -Wl,-rpath,$JULIA_DIR/lib test.c -ljulia
```

Alternatif olarak, `test/embedding/` klasöründeki Julia kaynak ağacındaki `embedding.c` programına bakın. `cli/loader_exe.c` dosyası, `libjulia` ile bağlantı kurarken `jl_options` seçeneklerini ayarlamanın başka bir basit örneğidir.

Julia'nın herhangi bir C fonksiyonunu çağırmadan önce yapılması gereken ilk şey, Julia'yı başlatmaktır. Bu, Julia'nın kurulum konumunu otomatik olarak belirlemeye çalışan `jl_init` çağrılarak yapılır. Özel bir konum belirtmeniz veya hangi sistem görüntüsünün yüklenmesi gerektiğini belirtmeniz gerekiyorsa, bunun yerine `jl_init_with_image` kullanın.

Test programındaki ikinci ifade, `jl_eval_string` çağrısını kullanarak bir Julia ifadesini değerlendirir.

Program sona ermeden önce, `jl_atexit_hook`'un çağrılması şiddetle tavsiye edilir. Yukarıdaki örnek program, `main`'den dönerken bunu çağırır.

!!! note
    Şu anda, `libjulia` paylaşımlı kütüphanesi ile dinamik bağlantı kurmak `RTLD_GLOBAL` seçeneğinin geçmesini gerektiriyor. Python'da bu şu şekilde görünür:

    ```
    >>> julia=CDLL('./libjulia.dylib',RTLD_GLOBAL)
    >>> julia.jl_init.argtypes = []
    >>> julia.jl_init()
    250593296
    ```


!!! note
    Eğer julia programı ana yürütülebilir dosyadan sembollere erişmesi gerekiyorsa, Linux'ta `julia-config.jl` tarafından aşağıda açıklananların yanı sıra derleme zamanında `-Wl,--export-dynamic` bağlayıcı bayrağını eklemek gerekebilir. Bu, paylaşılan bir kütüphane derlenirken gerekli değildir.


### Using julia-config to automatically determine build parameters

`julia-config.jl` beti, gömülü Julia kullanan bir programın ihtiyaç duyduğu yapılandırma parametrelerini belirlemeye yardımcı olmak için oluşturulmuştur. Bu betik, çağrıldığı belirli Julia dağıtımının yapılandırma parametrelerini ve sistem yapılandırmasını kullanarak, o dağıtımla etkileşimde bulunacak bir gömme programı için gerekli derleyici bayraklarını dışa aktarmak için kullanılır. Bu betik, Julia paylaşılan veri dizininde bulunmaktadır.

#### Example

```c
#include <julia.h>

int main(int argc, char *argv[])
{
    jl_init();
    (void)jl_eval_string("println(sqrt(2.0))");
    jl_atexit_hook(0);
    return 0;
}
```

#### On the command line

Bu scriptin basit bir kullanımı komut satırından yapılır. `julia-config.jl` dosyasının `/usr/local/julia/share/julia` konumunda bulunduğunu varsayarsak, doğrudan komut satırında çağrılabilir ve üç bayrağın herhangi bir kombinasyonunu alır:

```
/usr/local/julia/share/julia/julia-config.jl
Usage: julia-config [--cflags|--ldflags|--ldlibs]
```

Eğer yukarıdaki örnek kaynak `embed_example.c` dosyasında kaydedilmişse, aşağıdaki komut onu Linux ve Windows (MSYS2 ortamında) çalıştırılabilir bir programa derleyecektir. macOS'ta `gcc` yerine `clang` kullanın.:

```
/usr/local/julia/share/julia/julia-config.jl --cflags --ldflags --ldlibs | xargs gcc embed_example.c
```

#### Use in Makefiles

Genel olarak, gömme projeleri yukarıdaki örnekten daha karmaşık olacaktır ve bu nedenle aşağıdaki, genel makefile desteğine de izin vermektedir - **shell** makro genişletmelerinin kullanımı nedeniyle GNU make varsayılarak. Ayrıca, `julia-config.jl` genellikle `/usr/local` dizininde bulunsa da, eğer değilse, Julia kendisi `julia-config.jl`'yi bulmak için kullanılabilir ve makefile bundan faydalanabilir. Yukarıdaki örnek, bir makefile kullanacak şekilde genişletilmiştir:

```
JL_SHARE = $(shell julia -e 'print(joinpath(Sys.BINDIR, Base.DATAROOTDIR, "julia"))')
CFLAGS   += $(shell $(JL_SHARE)/julia-config.jl --cflags)
CXXFLAGS += $(shell $(JL_SHARE)/julia-config.jl --cflags)
LDFLAGS  += $(shell $(JL_SHARE)/julia-config.jl --ldflags)
LDLIBS   += $(shell $(JL_SHARE)/julia-config.jl --ldlibs)

all: embed_example
```

Artık derleme komutu basitçe `make`dir.

## High-Level Embedding on Windows with Visual Studio

Eğer `JULIA_DIR` ortam değişkeni ayarlanmamışsa, Visual Studio'yu başlatmadan önce Sistem panelini kullanarak ekleyin. JULIA_DIR altındaki `bin` klasörü sistem PATH'inde olmalıdır.

Visual Studio'yu açarak yeni bir Konsol Uygulaması projesi oluşturuyoruz. 'stdafx.h' başlık dosyasını açın ve sonuna aşağıdaki satırları ekleyin:

```c
#include <julia.h>
```

Sonra, projedeki main() fonksiyonunu bu kodla değiştirin:

```c
int main(int argc, char *argv[])
{
    /* required: setup the Julia context */
    jl_init();

    /* run Julia commands */
    jl_eval_string("print(sqrt(2.0))");

    /* strongly recommended: notify Julia that the
         program is about to terminate. this allows
         Julia time to cleanup pending write requests
         and run all finalizers
    */
    jl_atexit_hook(0);
    return 0;
}
```

Sonraki adım, projeyi Julia dahil dosyalarını ve kütüphaneleri bulacak şekilde ayarlamaktır. Julia kurulumunun 32 bit mi yoksa 64 bit mi olduğunu bilmek önemlidir. İlerlemeden önce, Julia kurulumuna uymayan herhangi bir platform yapılandırmasını kaldırın.

Proje Özellikleri iletişim kutusunu kullanarak, `C/C++` | `Genel` bölümüne gidin ve `$(JULIA_DIR)\include\julia\` ifadesini Ekstra Dahil Dizini özelliğine ekleyin. Ardından, `Bağlayıcı` | `Genel` bölümüne gidin ve `$(JULIA_DIR)\lib` ifadesini Ekstra Kütüphane Dizini özelliğine ekleyin. Son olarak, `Bağlayıcı` | `Girdi` altında, kütüphane listesine `libjulia.dll.a;libopenlibm.dll.a;` ifadesini ekleyin.

Bu noktada, proje derlenmeli ve çalıştırılmalıdır.

## Converting Types

Gerçek uygulamalar yalnızca ifadeleri yürütmekle kalmayacak, aynı zamanda değerlerini ana programa döndürmeleri gerekecektir. `jl_eval_string`, yığın üzerinde tahsis edilmiş bir Julia nesnesine işaret eden bir `jl_value_t*` döndürür. [`Float64`](@ref) gibi basit veri türlerini bu şekilde depolamak `boxing` olarak adlandırılır ve depolanan ilkel veriyi çıkarmak `unboxing` olarak adlandırılır. 2'nin karekökünü hesaplayan ve sonucu C'de geri okuyan geliştirilmiş örnek programımızın gövdesi artık bu kodu içermektedir:

```c
jl_value_t *ret = jl_eval_string("sqrt(2.0)");

if (jl_typeis(ret, jl_float64_type)) {
    double ret_unboxed = jl_unbox_float64(ret);
    printf("sqrt(2.0) in C: %e \n", ret_unboxed);
}
else {
    printf("ERROR: unexpected return type from sqrt(::Float64)\n");
}
```

`ret`'in belirli bir Julia türünde olup olmadığını kontrol etmek için `jl_isa`, `jl_typeis` veya `jl_is_...` fonksiyonlarını kullanabiliriz. Julia kabuğuna `typeof(sqrt(2.0))` yazarak dönen türün [`Float64`](@ref) (`C`'de `double`) olduğunu görebiliriz. Yukarıdaki kod parçasında kutulanmış Julia değerini C double'a dönüştürmek için `jl_unbox_float64` fonksiyonu kullanılır.

Karşılık gelen `jl_box_...` fonksiyonları diğer yöne dönüştürmek için kullanılır:

```c
jl_value_t *a = jl_box_float64(3.0);
jl_value_t *b = jl_box_float32(3.0f);
jl_value_t *c = jl_box_int32(3);
```

Gördüğümüz gibi, belirli argümanlarla Julia fonksiyonlarını çağırmak için boxing gereklidir.

## Calling Julia Functions

`jl_eval_string` C'ye bir Julia ifadesinin sonucunu elde etme imkanı tanırken, C'de hesaplanan argümanları Julia'ya geçirmeye izin vermez. Bunun için doğrudan Julia fonksiyonlarını çağırmanız gerekecek, `jl_call` kullanarak:

```c
jl_function_t *func = jl_get_function(jl_base_module, "sqrt");
jl_value_t *argument = jl_box_float64(2.0);
jl_value_t *ret = jl_call1(func, argument);
```

İlk adımda, `sqrt` Julia fonksiyonuna bir referans almak için `jl_get_function` çağrılır. `jl_get_function`'a geçirilen ilk argüman, `sqrt`'ın tanımlandığı `Base` modülüne bir işaretçidir. Ardından, double değeri `jl_box_float64` kullanılarak kutulanır. Son olarak, son adımda, fonksiyon `jl_call1` kullanılarak çağrılır. Farklı argüman sayılarıyla kolayca başa çıkmak için `jl_call0`, `jl_call2` ve `jl_call3` fonksiyonları da mevcuttur. Daha fazla argüman geçirmek için `jl_call` kullanın:

```
jl_value_t *jl_call(jl_function_t *f, jl_value_t **args, int32_t nargs)
```

İkinci argümanı `args`, `jl_value_t*` argümanlarının bir dizisidir ve `nargs` argüman sayısını belirtir.

Ayrıca, Julia fonksiyonlarını çağırmanın alternatif, muhtemelen daha basit bir yolu da [`@cfunction`](@ref) aracılığıyladır. `@cfunction` kullanmak, tip dönüşümlerini Julia tarafında yapmanıza olanak tanır, bu genellikle C tarafında yapmaktan daha kolaydır. Yukarıdaki `sqrt` örneği `@cfunction` ile şöyle yazılacaktır:

```c
double (*sqrt_jl)(double) = jl_unbox_voidpointer(jl_eval_string("@cfunction(sqrt, Float64, (Float64,))"));
double ret = sqrt_jl(2.0);
```

ilk olarak Julia'da C çağrılabilir bir fonksiyonu tanımladığımız, ardından ondan fonksiyon işaretçisini çıkardığımız ve nihayetinde onu çağırdığımız yerdir. Daha yüksek seviyeli dilde tür dönüşümlerini basitleştirmenin yanı sıra, Julia fonksiyonlarını `@cfunction` işaretçileri aracılığıyla çağırmak, tüm argümanların "kutulanmış" olduğu `jl_call` için gereken dinamik çağrı aşamasını ortadan kaldırır ve yerel C fonksiyon işaretçileri ile eşdeğer performansa sahip olmalıdır.

## Memory Management

Julia nesneleri C'de `jl_value_t*` türünde işaretçiler olarak temsil edilmektedir. Bu, bu nesneleri serbest bırakmaktan kimin sorumlu olduğu sorusunu gündeme getirir.

Genellikle, Julia nesneleri çöp toplayıcı (GC) tarafından serbest bırakılır, ancak GC, C'den bir Julia değerine bir referans tuttuğumuzu otomatik olarak bilmez. Bu, GC'nin nesneleri sizin altınızdan serbest bırakabileceği anlamına gelir ve bu da işaretçilerin geçersiz hale gelmesine yol açar.

GC yalnızca yeni Julia nesneleri tahsis edildiğinde çalışacaktır. `jl_box_float64` gibi çağrılar tahsisat yapar, ancak tahsisat, Julia kodu çalıştırılırken herhangi bir noktada da gerçekleşebilir.

Julia'yı gömülü olarak kullanırken, `jl_value_t*` değerlerini `jl_...` çağrıları arasında kullanmak genellikle güvenlidir (çünkü GC yalnızca bu çağrılar tarafından tetiklenir). Ancak, değerlerin `jl_...` çağrıları sırasında hayatta kalmasını sağlamak için, Julia'ya hala Julia [root](https://www.cs.purdue.edu/homes/hosking/690M/p611-fenichel.pdf) değerlerine bir referans tuttuğumuzu bildirmemiz gerekir; bu işleme "GC kökleme" denir. Bir değeri köklemek, çöp toplayıcının bu değeri yanlışlıkla kullanılmıyor olarak tanımlayıp bu değerin arkasındaki belleği serbest bırakmamasını sağlar. Bu, `JL_GC_PUSH` makroları kullanılarak yapılabilir:

```c
jl_value_t *ret = jl_eval_string("sqrt(2.0)");
JL_GC_PUSH1(&ret);
// Do something with ret
JL_GC_POP();
```

`JL_GC_POP` çağrısı, önceki `JL_GC_PUSH` ile kurulan referansları serbest bırakır. `JL_GC_PUSH`'un C yığınında referansları depoladığını unutmayın, bu nedenle kapsamdan çıkmadan önce tam olarak bir `JL_GC_POP` ile eşleştirilmelidir. Yani, fonksiyon dönmeden veya kontrol akışı, `JL_GC_PUSH`'un çağrıldığı bloktan başka bir yere gitmeden önce.

Birden fazla Julia değeri, `JL_GC_PUSH2` ile `JL_GC_PUSH6` makrolarını kullanarak aynı anda itilebilir:

```
JL_GC_PUSH2(&ret1, &ret2);
// ...
JL_GC_PUSH6(&ret1, &ret2, &ret3, &ret4, &ret5, &ret6);
```

Bir dizi Julia değerini itmek için `JL_GC_PUSHARGS` makrosu kullanılabilir, bu da şu şekilde kullanılabilir:

```c
jl_value_t **args;
JL_GC_PUSHARGS(args, 2); // args can now hold 2 `jl_value_t*` objects
args[0] = some_value;
args[1] = some_other_value;
// Do something with args (e.g. call jl_... functions)
JL_GC_POP();
```

Her bir kapsam yalnızca bir kez `JL_GC_PUSH*` çağrısına sahip olmalı ve yalnızca tek bir `JL_GC_POP` çağrısı ile eşleştirilmelidir. Eğer köklemek istediğiniz tüm gerekli değişkenler `JL_GC_PUSH*` ile tek bir çağrıda itilemeyecekse veya itilecek 6'dan fazla değişken varsa ve bir argüman dizisi kullanmak bir seçenek değilse, o zaman iç bloklar kullanılabilir:

```c
jl_value_t *ret1 = jl_eval_string("sqrt(2.0)");
JL_GC_PUSH1(&ret1);
jl_value_t *ret2 = 0;
{
    jl_function_t *func = jl_get_function(jl_base_module, "exp");
    ret2 = jl_call1(func, ret1);
    JL_GC_PUSH1(&ret2);
    // Do something with ret2.
    JL_GC_POP();    // This pops ret2.
}
JL_GC_POP();    // This pops ret1.
```

Not edin ki, `JL_GC_PUSH*` çağırmadan önce geçerli `jl_value_t*` değerlerine sahip olmak gerekli değildir. Birkaçını `NULL` olarak başlatmak, bunları `JL_GC_PUSH*`'a geçirmek ve ardından gerçek Julia değerlerini oluşturmak sorun değildir. Örneğin:

```
jl_value_t *ret1 = NULL, *ret2 = NULL;
JL_GC_PUSH2(&ret1, &ret2);
ret1 = jl_eval_string("sqrt(2.0)");
ret2 = jl_eval_string("sqrt(3.0)");
// Use ret1 and ret2
JL_GC_POP();
```

Eğer bir değişkenin işaretçisini fonksiyonlar (veya blok kapsamları) arasında tutmak gerekiyorsa, `JL_GC_PUSH*` kullanmak mümkün değildir. Bu durumda, değişkenin Julia küresel kapsamında bir referans oluşturmak ve saklamak gereklidir. Bunu başarmanın basit bir yolu, referansları tutacak ve GC tarafından bellekten atılmayı önleyecek küresel bir `IdDict` kullanmaktır. Ancak, bu yöntem yalnızca değiştirilebilir türlerle düzgün çalışacaktır.

```c
// This functions shall be executed only once, during the initialization.
jl_value_t* refs = jl_eval_string("refs = IdDict()");
jl_function_t* setindex = jl_get_function(jl_base_module, "setindex!");

...

// `var` is the variable we want to protect between function calls.
jl_value_t* var = 0;

...

// `var` is a `Vector{Float64}`, which is mutable.
var = jl_eval_string("[sqrt(2.0); sqrt(4.0); sqrt(6.0)]");

// To protect `var`, add its reference to `refs`.
jl_call3(setindex, refs, var, var);
```

Eğer değişken değişmezse, o zaman `IdDict`'ye itmeden önce eşdeğer bir değiştirilebilir konteyner veya tercihen `RefValue{Any}` içine sarılması gerekir. Bu yaklaşımda, konteynerin C kodu aracılığıyla, örneğin `jl_new_struct` fonksiyonu kullanılarak oluşturulması veya doldurulması gerekir. Eğer konteyner `jl_call*` ile oluşturulursa, o zaman C kodunda kullanılmak üzere işaretçinin yeniden yüklenmesi gerekecektir.

```c
// This functions shall be executed only once, during the initialization.
jl_value_t* refs = jl_eval_string("refs = IdDict()");
jl_function_t* setindex = jl_get_function(jl_base_module, "setindex!");
jl_datatype_t* reft = (jl_datatype_t*)jl_eval_string("Base.RefValue{Any}");

...

// `var` is the variable we want to protect between function calls.
jl_value_t* var = 0;

...

// `var` is a `Float64`, which is immutable.
var = jl_eval_string("sqrt(2.0)");

// Protect `var` until we add its reference to `refs`.
JL_GC_PUSH1(&var);

// Wrap `var` in `RefValue{Any}` and push to `refs` to protect it.
jl_value_t* rvar = jl_new_struct(reft, var);
JL_GC_POP();

jl_call3(setindex, refs, rvar, rvar);
```

GC, bir değişkenin referansını `refs`'ten `delete!` fonksiyonu ile kaldırarak değişkeni serbest bırakmasına izin verilebilir, yeter ki değişkenin başka bir yerde tutulmuş başka bir referansı olmasın:

```c
jl_function_t* delete = jl_get_function(jl_base_module, "delete!");
jl_call2(delete, refs, rvar);
```

Çok basit durumlar için alternatif olarak, sadece `Vector{Any}` türünde bir global konteyner oluşturmak ve gerektiğinde o konteynerden elemanları almak mümkündür; ya da her bir işaretçi için bir global değişken oluşturmak da mümkündür.

```c
jl_module_t *mod = jl_main_module;
jl_sym_t *var = jl_symbol("var");
jl_binding_t *bp = jl_get_binding_wr(mod, var, 1);
jl_checked_assignment(bp, mod, var, val);
```

### Updating fields of GC-managed objects

Çöp toplayıcı, her zaman daha eski nesil bir nesnenin daha genç nesil bir nesneye işaret ettiğini bildiği varsayımı altında da çalışır. Bu varsayımı bozan bir işaretçi güncellendiğinde, bu durum `jl_gc_wb` (yazma engeli) fonksiyonu ile toplayıcıya bildirilmelidir:

```c
jl_value_t *parent = some_old_value, *child = some_young_value;
((some_specific_type*)parent)->field = child;
jl_gc_wb(parent, child);
```

Genel olarak, hangi değerlerin çalışma zamanında eski olacağını tahmin etmek imkansızdır, bu nedenle yazma engeli tüm açık depolamalardan sonra eklenmelidir. Dikkate değer bir istisna, `parent` nesnesinin yeni tahsis edilmiş olması ve o zamandan beri hiçbir çöp toplama işleminin yapılmamış olmasıdır. Çoğu `jl_...` fonksiyonunun bazen çöp toplama işlemini tetikleyebileceğini unutmayın.

Yazı engeli, doğrudan verilerini güncellerken işaretçi dizileri için de gereklidir. `jl_array_ptr_set` çağrısı genellikle çok daha tercih edilir. Ancak doğrudan güncellemeler yapılabilir. Örneğin:

```c
jl_array_t *some_array = ...; // e.g. a Vector{Any}
void **data = jl_array_data(some_array, void*);
jl_value_t *some_value = ...;
data[0] = some_value;
jl_gc_wb(jl_array_owner(some_array), some_value);
```

### Controlling the Garbage Collector

GC'yi kontrol etmek için bazı işlevler vardır. Normal kullanım durumlarında, bunlar gerekli olmamalıdır.

| Function             | Description                                  |
|:-------------------- |:-------------------------------------------- |
| `jl_gc_collect()`    | Force a GC run                               |
| `jl_gc_enable(0)`    | Disable the GC, return previous state as int |
| `jl_gc_enable(1)`    | Enable the GC,  return previous state as int |
| `jl_gc_is_enabled()` | Return current state as int                  |

## Working with Arrays

Julia ve C, dizi verilerini kopyalamadan paylaşabilir. Bir sonraki örnek bunun nasıl çalıştığını gösterecektir.

Julia dizileri C'de `jl_array_t*` veri tipiyle temsil edilir. Temelde, `jl_array_t` bir yapı (struct) olup şunları içerir:

  * Veri tipi hakkında bilgi
  * Veri bloğuna bir işaretçi
  * Dizi boyutları hakkında bilgi

Basit tutmak için, 1D bir dizi ile başlıyoruz. Uzunluğu 10 olan Float64 elemanları içeren bir dizi oluşturmak şöyle yapılabilir:

```c
jl_value_t* array_type = jl_apply_array_type((jl_value_t*)jl_float64_type, 1);
jl_array_t* x          = jl_alloc_array_1d(array_type, 10);
```

Alternatif olarak, eğer diziyi zaten ayırdıysanız, verileri etrafında ince bir sarmalayıcı oluşturabilirsiniz:

```c
double *existingArray = (double*)malloc(sizeof(double)*10);
jl_array_t *x = jl_ptr_to_array_1d(array_type, existingArray, 10, 0);
```

Son argüman, Julia'nın verinin mülkiyetini alıp almayacağını belirten bir boolean'dır. Bu argüman sıfırdan farklıysa, GC veri işaretçisi üzerinde `free` çağrısı yapacaktır, böylece dizi artık referans edilmediğinde.

`x` verilerine erişmek için `jl_array_data` kullanabiliriz:

```c
double *xData = jl_array_data(x, double);
```

Artık diziyi doldurabiliriz:

```c
for (size_t i = 0; i < jl_array_nrows(x); i++)
    xData[i] = i;
```

Şimdi `x` üzerinde yerinde bir işlem gerçekleştiren bir Julia fonksiyonunu çağıralım:

```c
jl_function_t *func = jl_get_function(jl_base_module, "reverse!");
jl_call1(func, (jl_value_t*)x);
```

Diziyi yazdırarak, `x`'in elemanlarının artık tersine döndüğünü doğrulayabilirsiniz.

### Accessing Returned Arrays

Eğer bir Julia fonksiyonu bir dizi döndürüyorsa, `jl_eval_string` ve `jl_call`'ın döndürdüğü değer bir `jl_array_t*`'ye dönüştürülebilir:

```c
jl_function_t *func  = jl_get_function(jl_base_module, "reverse");
jl_array_t *y = (jl_array_t*)jl_call1(func, (jl_value_t*)x);
```

Artık `y`'nin içeriğine daha önce olduğu gibi `jl_array_data` kullanarak erişilebilir. Her zamanki gibi, dizi kullanılırken bir referans tutmayı unutmayın.

### Multidimensional Arrays

Julia'nın çok boyutlu dizileri bellekte sütun öncelikli sırayla saklanır. İşte bir 2D dizi oluşturan ve özelliklerine erişen bazı kodlar:

```c
// Create 2D array of float64 type
jl_value_t *array_type = jl_apply_array_type((jl_value_t*)jl_float64_type, 2);
int dims[] = {10,5};
jl_array_t *x  = jl_alloc_array_nd(array_type, dims, 2);

// Get array pointer
double *p = jl_array_data(x, double);
// Get number of dimensions
int ndims = jl_array_ndims(x);
// Get the size of the i-th dim
size_t size0 = jl_array_dim(x,0);
size_t size1 = jl_array_dim(x,1);

// Fill array with data
for(size_t i=0; i<size1; i++)
    for(size_t j=0; j<size0; j++)
        p[j + size0*i] = i + j;
```

Dikkat edin ki, Julia dizileri 1 tabanlı indeksleme kullanırken, C API'si 0 tabanlı indeksleme kullanır (örneğin, `jl_array_dim` çağrısında) ve bu, C kodu olarak alışıldık bir şekilde okunmasını sağlar.

## Exceptions

Julia kodu istisnalar fırlatabilir. Örneğin, dikkate alalım:

```c
jl_eval_string("this_function_does_not_exist()");
```

Bu çağrı hiçbir şey yapıyormuş gibi görünecek. Ancak, bir istisnanın atılıp atılmadığını kontrol etmek mümkündür:

```c
if (jl_exception_occurred())
    printf("%s \n", jl_typeof_str(jl_exception_occurred()));
```

Eğer istisnaları destekleyen bir dilden (örneğin Python, C#, C++) Julia C API'sini kullanıyorsanız, `libjulia`'ya yapılan her çağrıyı, bir istisna atılıp atılmadığını kontrol eden ve ardından istisnayı ana dilde yeniden fırlatan bir fonksiyonla sarmak mantıklıdır.

### Throwing Julia Exceptions

Julia callable fonksiyonları yazarken, argümanları doğrulamak ve hataları belirtmek için istisnalar fırlatmak gerekebilir. Tipik bir tür kontrolü şöyle görünür:

```c
if (!jl_typeis(val, jl_float64_type)) {
    jl_type_error(function_name, (jl_value_t*)jl_float64_type, val);
}
```

Genel istisnalar aşağıdaki fonksiyonlar kullanılarak oluşturulabilir:

```c
void jl_error(const char *str);
void jl_errorf(const char *fmt, ...);
```

`jl_error` bir C dizesi alır ve `jl_errorf` `printf` gibi çağrılır:

```c
jl_errorf("argument x = %d is too large", x);
```

bu örnekte `x`'in bir tam sayı olduğu varsayılmaktadır.

### Thread-safety

Genel olarak, Julia C API'si tam olarak thread-safe değildir. Julia'yı çok iş parçacıklı bir uygulamaya gömüldüğünde, aşağıdaki kısıtlamaların ihlal edilmemesine dikkat edilmelidir:

  * `jl_init()` uygulama ömründe yalnızca bir kez çağrılabilir. `jl_atexit_hook()` için de aynı durum geçerlidir ve yalnızca `jl_init()`'den sonra çağrılabilir.
  * `jl_...()` API işlevleri yalnızca `jl_init()`'in çağrıldığı thread'den veya Julia çalışma zamanının başlattığı thread'lerden çağrılabilir. Kullanıcı tarafından başlatılan thread'lerden Julia API işlevlerinin çağrılması desteklenmez ve belirsiz davranışlara ve çöküşlere yol açabilir.

Yukarıdaki ikinci koşul, `jl_...()` fonksiyonlarını Julia tarafından başlatılmamış olan thread'lerden güvenli bir şekilde çağırmanın mümkün olmadığını ima eder (bu durumda `jl_init()` çağrısını yapan thread istisnadır). Örneğin, aşağıdaki desteklenmemekte ve büyük olasılıkla segfault verecektir:

```c
void *func(void*)
{
    // Wrong, jl_eval_string() called from thread that was not started by Julia
    jl_eval_string("println(Threads.threadid())");
    return NULL;
}

int main()
{
    pthread_t t;

    jl_init();

    // Start a new thread
    pthread_create(&t, NULL, func, NULL);
    pthread_join(t, NULL);

    jl_atexit_hook(0);
}
```

Bunun yerine, tüm Julia çağrılarını aynı kullanıcı tarafından oluşturulan iş parçacığından yapmak işe yarayacaktır:

```c
void *func(void*)
{
    // Okay, all jl_...() calls from the same thread,
    // even though it is not the main application thread
    jl_init();
    jl_eval_string("println(Threads.threadid())");
    jl_atexit_hook(0);
    return NULL;
}

int main()
{
    pthread_t t;
    // Create a new thread, which runs func()
    pthread_create(&t, NULL, func, NULL);
    pthread_join(t, NULL);
}
```

Julia'nın kendisi tarafından başlatılan bir iş parçacığından Julia C API'sini çağırmanın bir örneği:

```c
#include <julia/julia.h>
JULIA_DEFINE_FAST_TLS

double c_func(int i)
{
    printf("[C %08x] i = %d\n", pthread_self(), i);

    // Call the Julia sqrt() function to compute the square root of i, and return it
    jl_function_t *sqrt = jl_get_function(jl_base_module, "sqrt");
    jl_value_t* arg = jl_box_int32(i);
    double ret = jl_unbox_float64(jl_call1(sqrt, arg));

    return ret;
}

int main()
{
    jl_init();

    // Define a Julia function func() that calls our c_func() defined in C above
    jl_eval_string("func(i) = ccall(:c_func, Float64, (Int32,), i)");

    // Call func() multiple times, using multiple threads to do so
    jl_eval_string("println(Threads.threadpoolsize())");
    jl_eval_string("use(i) = println(\"[J $(Threads.threadid())] i = $(i) -> $(func(i))\")");
    jl_eval_string("Threads.@threads for i in 1:5 use(i) end");

    jl_atexit_hook(0);
}
```

Eğer bu kodu 2 Julia iş parçacığı ile çalıştırırsak, aşağıdaki çıktıyı alırız (not: çıktı her çalıştırmada ve sistemde değişiklik gösterecektir):

```sh
$ JULIA_NUM_THREADS=2 ./thread_example
2
[C 3bfd9c00] i = 1
[C 23938640] i = 4
[J 1] i = 1 -> 1.0
[C 3bfd9c00] i = 2
[J 1] i = 2 -> 1.4142135623730951
[C 3bfd9c00] i = 3
[J 2] i = 4 -> 2.0
[C 23938640] i = 5
[J 1] i = 3 -> 1.7320508075688772
[J 2] i = 5 -> 2.23606797749979
```

Görüldüğü gibi, Julia iş parçacığı 1, pthread ID 3bfd9c00 ile, Julia iş parçacığı 2 ise ID 23938640 ile ilişkilidir. Bu, gerçekten de C seviyesinde birden fazla iş parçacığının kullanıldığını ve bu iş parçacıklarından Julia C API rutinlerini güvenle çağırabileceğimizi göstermektedir.
