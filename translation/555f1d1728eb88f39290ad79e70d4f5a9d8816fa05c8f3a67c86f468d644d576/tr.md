# External Profiler Support

Julia, bazı dış izleme profilleyicileri için açık destek sağlar ve bu sayede çalışma zamanının yürütme davranışının yüksek düzeyde bir genel görünümünü elde etmenizi sağlar.

Desteklenen profiller şunlardır:

  * [Tracy](https://github.com/wolfpld/tracy)
  * [Intel VTune (ITTAPI)](https://github.com/intel/ittapi)

### Adding New Zones

Yeni bölgeler eklemek için `JL_TIMING` makrosunu kullanın. `JL_TIMING` arayarak kod tabanında birçok örnek bulabilirsiniz. Yeni bir bölge türü eklemek için bunu `JL_TIMING_OWNERS`'a (ve muhtemelen `JL_TIMING_EVENTS`'a) eklemeniz gerekir.

### Dynamically Enabling and Disabling Zones

[`JULIA_TIMING_SUBSYSTEMS`](@ref JULIA_TIMING_SUBSYSTEMS) ortam değişkeni, belirli bir Julia çalışması için bölgeleri etkinleştirmenizi veya devre dışı bırakmanızı sağlar. Örneğin, değişkeni `+GC,-INFERENCE` olarak ayarlamak, `GC` bölgelerini etkinleştirir ve `INFERENCE` bölgelerini devre dışı bırakır.

## Tracy Profiler

[Tracy](https://github.com/wolfpld/tracy) Julia ile isteğe bağlı olarak entegre edilebilen esnek bir profildir.

Tipik bir Tracy oturumu şöyle görünebilir:

![Tipik Tracy kullanımı](tracy.png)

### Building Julia with Tracy

Tracy entegrasyonunu etkinleştirmek için, `Make.user` dosyasında `WITH_TRACY=1` ekstra seçeneği ile Julia'yı derleyin.

### Installing the Tracy Profile Viewer

Profil görüntüleyicisini elde etmenin en kolay yolu `TracyProfiler_jll` paketini eklemek ve profili başlatmaktır:

```julia
run(TracyProfiler_jll.tracy())
```

!!! note
    macOS'ta, profilerdeki UI öğeleri aşırı büyük görünüyorsa `TRACY_DPI_SCALE` ortam değişkenini `1.0` olarak ayarlamak isteyebilirsiniz.


"Başsız" bir örneği çalıştırmak ve izleme verilerini diske kaydetmek için, kullanın

```julia
run(`$(TracyProfiler_jll.capture()) -o mytracefile.tracy`)
```

bunun yerine.

Tracy arayüzünü kullanma hakkında bilgi için Tracy kılavuzuna başvurun.

### Profiling Julia with Tracy

Bir Tracy ile Julia profil oluşturma için tipik bir iş akışı, Julia'yı şu şekilde başlatmayı içerir:

```julia
JULIA_WAIT_FOR_TRACY=1 ./julia -e '...'
```

Çevre değişkeni, Julia'nın Tracy profilleme aracına başarıyla bağlanana kadar beklemesini sağlar. Daha sonra, Tracy profilleme arayüzünü kullanarak `Bağlan` butonuna tıklayın ve Julia'nın çalışması devam etmeli ve profilleme başlamalıdır.

### Profiling package precompilation with Tracy

Bir paketin ön derleme sürecini profil etmek için, ön derlemek istediğiniz paketi `Base.compilecache` içine açıkça çağırmak en kolay yoldur:

```julia
pkg = Base.identify_package("SparseArrays")
withenv("JULIA_WAIT_FOR_TRACY" => 1, "TRACY_PORT" => 9001) do
    Base.compilecache(pkg)
end
```

Burada, Tracy UI'de bağlanmak için doğru istemciyi bulmayı kolaylaştıran özel bir port kullanıyoruz.

### Adding metadata to zones

`jl_timing_show_*` ve `jl_timing_printf` fonksiyonları, bir bölgeye bir (veya birden fazla) dize eklemek için kullanılabilir. Örneğin, çıkarım için izleme bölgesi, çıkarımı yapılan yöntem örneğini gösterir.

`TracyCZoneColor` fonksiyonu, belirli bir bölgenin rengini ayarlamak için kullanılabilir. Kod tabanında nasıl kullanıldığını görmek için arama yapın.

### Viewing Tracy files in your browser

https://topolarity.github.io/trace-viewer/ adresini ziyaret edin, Tracy izleri için (deneysel) bir web görüntüleyici.

Yerel bir `.tracy` dosyasını açabilir veya web'den bir URL sağlayabilirsiniz (örneğin, bir Github deposundaki bir dosya). Web'den bir iz dosyası yüklediğinizde, aynı iz dosyasını görüntülemeleri için başkalarıyla sayfa URL'sini de paylaşabilirsiniz.

### Enabling stack trace samples

Tracy'de çağrı yığını örneklemeyi etkinleştirmek için, `Make.user` dosyanızda Julia'yı bu seçeneklerle derleyin:

```
WITH_TRACY := 1
WITH_TRACY_CALLSTACKS := 1
USE_BINARYBUILDER_LIBTRACYCLIENT := 0
```

`make -C deps clean-libtracyclient` komutunu çalıştırmanız da gerekebilir, böylece Tracy'nin yeniden derlenmesini zorlayabilirsiniz.

Bu özellik, iz boyutu ve profil oluşturma yükü üzerinde önemli bir etkiye sahiptir, bu nedenle, özellikle iz dosyalarınızı çevrimiçi paylaşmayı planlıyorsanız, çağrı yığını örneklemesini mümkünse kapalı bırakmanız önerilir.

Julia JIT çalışma zamanı henüz Tracy'nin sembolizasyonu için entegrasyona sahip olmadığından, Julia fonksiyonları genellikle bu yığın izlerinde bilinmeyen olacaktır.

## Intel VTune (ITTAPI) Profiler

*Bu bölüm henüz yazılmadı.*
