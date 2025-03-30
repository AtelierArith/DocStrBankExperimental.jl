# Instrumenting Julia with DTrace, and bpftrace

DTrace ve bpftrace, süreçlerin hafif enstrümantasyonunu sağlayan araçlardır. Enstrümantasyonu, süreç çalışırken açıp kapatabilirsiniz ve enstrümantasyon kapalıyken ek yük minimumdur.

!!! compat "Julia 1.8"
    Problar için destek Julia 1.8'de eklendi.


!!! note
    Bu belgeler, bir Linux perspektifinden yazılmıştır; çoğu, Mac OS/Darwin ve FreeBSD'de de geçerli olmalıdır.


## Enabling support

Linux'ta `dtrace` sürümüne sahip `systemtap` paketini kurun ve aşağıdaki içeriği barındıran bir `Make.user` dosyası oluşturun.

```
WITH_DTRACE=1
```

USDT probelerini etkinleştirmek için.

### Verifying

```
> readelf -n usr/lib/libjulia-internal.so.1

Displaying notes found in: .note.gnu.build-id
  Owner                Data size  Description
  GNU                  0x00000014 NT_GNU_BUILD_ID (unique build ID bitstring)
    Build ID: 57161002f35548772a87418d2385c284ceb3ead8

Displaying notes found in: .note.stapsdt
  Owner                Data size  Description
  stapsdt              0x00000029 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__begin
    Location: 0x000000000013213e, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cac
    Arguments:
  stapsdt              0x00000032 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__stop_the_world
    Location: 0x0000000000132144, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cae
    Arguments:
  stapsdt              0x00000027 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__end
    Location: 0x000000000013214a, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cb0
    Arguments:
  stapsdt              0x0000002d NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__finalizer
    Location: 0x0000000000132150, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cb2
    Arguments:
```

## Adding probes in libjulia

Problar, `src/uprobes.d` dosyasındaki dtrace formatında tanımlanır. Oluşturulan başlık dosyası `src/julia_internal.h` dosyasına dahil edilir ve eğer prob ekliyorsanız, burada bir noop uygulaması sağlamalısınız.

Başlık, bir semaphore `*_ENABLED` içerecek ve probe'a yapılan gerçek çağrıyı içerecektir. Eğer probe argümanları hesaplamak için pahalıysa, önce probe'un etkin olup olmadığını kontrol etmeli, ardından argümanları hesaplayıp probe'u çağırmalısınız.

```c
  if (JL_PROBE_{PROBE}_ENABLED())
    auto expensive_arg = ...;
    JL_PROBE_{PROBE}(expensive_arg);
```

Eğer probunuzun argümanı yoksa, semafor kontrolünü dahil etmemek tercih edilir. USDT probeleri etkinleştirildiğinde, bir semaforun maliyeti, probun etkin olup olmadığına bakılmaksızın bir bellek yüklemesidir.

```c
#define JL_PROBE_GC_BEGIN_ENABLED() __builtin_expect (julia_gc__begin_semaphore, 0)
__extension__ extern unsigned short julia_gc__begin_semaphore __attribute__ ((unused)) __attribute__ ((section (".probes")));
```

Probe kendisi, prob işleyicisine bir trambolin ile yamanacak bir noop kızak.

## Available probes

### GC probes

1. `julia:gc__begin`: GC bir iş parçacığında çalışmaya başlar ve dünyayı durdurma tetikler.
2. `julia:gc__stop_the_world`: Tüm iş parçacıkları bir güvenli noktaya ulaştı ve GC çalışıyor.
3. `julia:gc__mark__begin`: İşaretleme aşamasının başlangıcı
4. `julia:gc__mark_end(scanned_bytes, perm_scanned)`: İşaretleme aşaması sona erdi
5. `julia:gc__sweep_begin(full)`: Süpürme başlatılıyor
6. `julia:gc__sweep_end`: Süpürme aşaması tamamlandı
7. `julia:gc__end`: GC tamamlandı, diğer iş parçacıkları çalışmaya devam ediyor
8. `julia:gc__finalizer`: İlk GC iş parçacığı sonlandırıcıları çalıştırmayı tamamladı

### Task runtime probes

1. `julia:rt__run__task(task)`: Mevcut iş parçacığında `task` görevine geçiş yapılıyor.
2. `julia:rt__pause__task(task)`: Mevcut iş parçacığında `task` işine geçiş yapılıyor.
3. `julia:rt__new__task(parent, child)`: Görev `parent`, mevcut iş parçacığında `child` görevini oluşturdu.
4. `julia:rt__start__task(task)`: Görev `task`, yeni bir yığın ile ilk kez başlatıldı.
5. `julia:rt__finish__task(task)`: Görev `task` tamamlandı ve artık çalışmayacak.
6. `julia:rt__start__process__events(task)`: Görev `task`, libuv olaylarını işlemeye başladı.
7. `julia:rt__finish__process__events(task)`: Görev `task` libuv olaylarını işleme tamamladı.

### Task queue probes

1. `julia:rt__taskq__insert(ptls, task)`: Thread `ptls`, `task`'ı bir PARTR çoklu kuyruğa eklemeye çalıştı.
2. `julia:rt__taskq__get(ptls, task)`: Thread `ptls`, bir PARTR çoklu kuyruğundan `task`'ı çıkardı.

### Thread sleep/wake probes

1. `julia:rt__sleep__check__wake(ptls, eski_durum)`: İş parçacığı (PTLS `ptls`) uyanıyor, daha önce `eski_durum` durumundaydı.
2. `julia:rt__sleep__check__wakeup(ptls)`: İş parçacığı (PTLS `ptls`) kendini uyandırdı.
3. `julia:rt__sleep__check__sleep(ptls)`: İş parçacığı (PTLS `ptls`) uyumaya çalışıyor.
4. `julia:rt__sleep__check__taskq__wake(ptls)`: Thread (PTLS `ptls`) PARTR çoklu kuyruğundaki görevler nedeniyle uyumayı başaramadı.
5. `julia:rt__sleep__check__task__wake(ptls)`: İş parçacığı (PTLS `ptls`), Base iş kuyruğundaki görevler nedeniyle uyumayı başaramadı.
6. `julia:rt__sleep__check__uv__wake(ptls)`: Thread (PTLS `ptls`) libuv uyanma nedeniyle uyuyamıyor.

## Probe usage examples

### GC stop-the-world latency

Bir örnek `bpftrace` betiği `contrib/gc_stop_the_world_latency.bt` dosyasında verilmiştir ve bu, tüm iş parçacıklarının bir güvenli noktaya ulaşma gecikmesinin histogramını oluşturur.

Bu Julia kodunu `julia -t 2` ile çalıştırmak

```
using Base.Threads

fib(x) = x <= 1 ? 1 : fib(x-1) + fib(x-2)

beaver = @spawn begin
    while true
        fib(30)
        # A manual safepoint is necessary since otherwise this loop
        # may never yield to GC.
        GC.safepoint()
    end
end

allocator = @spawn begin
    while true
        zeros(1024)
    end
end

wait(allocator)
```

ve ikinci bir terminalde

```
> sudo contrib/bpftrace/gc_stop_the_world_latency.bt
Attaching 4 probes...
Tracing Julia GC Stop-The-World Latency... Hit Ctrl-C to end.
^C


@usecs[1743412]:
[4, 8)               971 |@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@|
[8, 16)              837 |@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@        |
[16, 32)             129 |@@@@@@                                              |
[32, 64)              10 |                                                    |
[64, 128)              1 |                                                    |
```

Durdurulan dünya aşamasının gecikme dağılımını yürütülen Julia sürecinde görebiliriz.

### Task spawn monitor

Bazen bir görevin diğer görevleri başlattığını bilmek faydalı olabilir. Bu, `rt__new__task` ile çok kolay bir şekilde görülebilir. Probenin ilk argümanı olan `parent`, yeni bir görev oluşturan mevcut görevdir. Bu, izlemek istediğiniz görevin adresini biliyorsanız, o belirli görevin başlattığı görevleri kolayca görebileceğiniz anlamına gelir. Bunu nasıl yapacağımıza bakalım; önce bir Julia oturumu başlatalım ve PID ile REPL'nin görev adresini alalım:

```
> julia
               _
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.6.2 (2021-07-14)
 _/ |\__'_|_|_|\__'_|  |  Official https://julialang.org/ release
|__/                   |

1> getpid()
997825

2> current_task()
Task (runnable) @0x00007f524d088010
```

Artık `bpftrace`'i başlatabiliriz ve yalnızca bu ebeveyn için `rt__new__task`'ı izleyebiliriz:

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__new__task /arg0==0x00007f524d088010/{ printf("Görev: %x\n", arg0); }'`

(Burada `arg0` ilk argümandır, `parent`).

Ve tek bir görev oluşturursak:

`@async 1+1`

bu görevin oluşturulduğunu görüyoruz:

`Görev: 4d088010`

Ancak, o yeni oluşturulan görevden bir sürü görev başlatırsak:

```julia
@async for i in 1:10
   @async 1+1
end
```

`bpftrace`'ten yalnızca bir görevi hala görüyoruz:

`Görev: 4d088010`

ve ve hala izlediğimiz aynı görev! Elbette, bu filtreyi kaldırarak *tüm* yeni oluşturulan görevleri görmek de bu kadar kolay:

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__new__task { printf("Görev: %x\n", arg0); }'`

```
Task: 4d088010
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
```

Kök görevimizi ve on tane daha yeni görevin ebeveyni olarak yeni oluşturulan görevi görebiliyoruz.

### Thundering herd detection

Görev süreleri genellikle "gürültülü sürü" sorunundan muzdarip olabilir: sessiz bir görev süresine bazı işler eklendiğinde, her bir iş parçacığının işleyebileceğinden daha fazla iş olmasa bile, tüm iş parçacıkları uykularından uyanabilir. Bu, tüm iş parçacıkları uyanırken (ve aynı anda uykuya geri dönerken, iş bulamadıklarında) ekstra gecikmelere ve CPU döngülerine neden olabilir.

Bu sorunu `bpftrace` ile oldukça kolay bir şekilde görebiliriz. Öncelikle, bir terminalde bu örnekte 6 olan çoklu iş parçacığı ile Julia'yı başlatıyoruz ve o işlemin PID'sini alıyoruz:

```
> julia -t 6
               _
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.6.2 (2021-07-14)
 _/ |\__'_|_|_|\__'_|  |  Official https://julialang.org/ release
|__/                   |

1> getpid()
997825
```

Ve başka bir terminalde `bpftrace` ile sürecimizi izlemeye başlıyoruz, özellikle `rt__sleep__check__wake` kancasını sorguluyoruz:

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__sleep__check__wake { printf("İş parçacığı uyandı! %x\n", arg0); }'`

Şimdi, Julia'da tek bir görev oluşturup çalıştırıyoruz:

`Threads.@spawn 1+1`

Ve `bpftrace` içinde şöyle bir şey yazdırıldığını görüyoruz:

```
Thread wake up! 3f926100
Thread wake up! 3ebd5140
Thread wake up! 3f876130
Thread wake up! 3e2711a0
Thread wake up! 3e312190
```

Tek bir görevi (sadece bir iş parçacığının aynı anda işleyebileceği) başlatmış olsak da, diğer tüm iş parçacıklarımızı uyandırdık! Gelecekte, daha akıllı bir görev çalışma zamanı yalnızca bir iş parçacığını (veya hiçbiri; başlatan iş parçacığı bu görevi yerine getirebilir!) uyandırabilir ve bu davranışın ortadan kalktığını görmeliyiz.

### Task Monitor with BPFnative.jl

BPFnative.jl, USDT prob noktalarına `bpftrace` gibi bağlanabilir. Görev çalışma süresi, GC ve iş parçacığı uyku/uyanma geçişlerini izlemek için bir demo mevcuttur [here](https://github.com/jpsamaroo/BPFnative.jl/blob/master/examples/task-runtime.jl).

## Notes on using `bpftrace`

bpftrace formatında bir örnek prob şöyle görünür:

```
usdt:usr/lib/libjulia-internal.so:julia:gc__begin
{
  @start[pid] = nsecs;
}
```

Probe bildirimi `usdt` türünü alır, ardından ya kütüphanenin yolu ya da PID, sağlayıcı adı `julia` ve prob adı `gc__begin` gelir. `libjulia-internal.so` için göreceli bir yol kullandığımı unutmayın, ancak bu, bir üretim sisteminde mutlak bir yol olması gerekebilir.

## Useful references:

  * [Julia Evans blog on Linux tracing systems](https://jvns.ca/blog/2017/07/05/linux-tracing-systems)
  * [LWN article on USDT and BPF](https://lwn.net/Articles/753601/)
  * [GDB support for probes](https://sourceware.org/gdb/onlinedocs/gdb/Static-Probe-Points.html)
  * [Brendan Gregg – Linux Performance](https://www.brendangregg.com/linuxperf.html)
