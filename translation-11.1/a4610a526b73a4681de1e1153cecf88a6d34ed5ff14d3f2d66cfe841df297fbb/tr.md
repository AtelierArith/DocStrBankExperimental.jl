```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Profile/docs/src/index.md"
```

# [Profiling](@id lib-profiling)

## CPU Profiling

CPU profilinin julia kodunu analiz etmenin iki ana yaklaşımı vardır:

## Via `@profile`

Veri bir çağrı için `@profile` makrosu aracılığıyla profil oluşturmanın etkin olduğu yer.

```julia-repl
julia> using Profile

julia> @profile foo()

julia> Profile.print()
Overhead ╎ [+additional indent] Count File:Line; Function
=========================================================
    ╎147  @Base/client.jl:506; _start()
        ╎ 147  @Base/client.jl:318; exec_options(opts::Base.JLOptions)
...
```

## Triggered During Execution

Zaten çalışan görevler, kullanıcı tarafından tetiklenen herhangi bir zamanda sabit bir süre boyunca da profil oluşturulabilir.

Profiling'i tetiklemek için:

  * MacOS ve FreeBSD (BSD tabanlı platformlar): `ctrl-t` kullanın veya julia sürecine bir `SIGINFO` sinyali gönderin, yani `% kill -INFO $julia_pid`
  * Linux: `julia` sürecine `SIGUSR1` sinyali gönderin, yani `% kill -USR1 $julia_pid`
  * Windows: Şu anda desteklenmiyor.

İlk olarak, sinyalin atıldığı anda tek bir yığın izinin gösterildiği, ardından 1 saniyelik bir profilin toplandığı ve sonraki yield noktasında profil raporunun verildiği, yield noktaları olmayan kodlar için görev tamamlanmasında (örneğin, sıkı döngüler) olabileceği belirtilmektedir.

İsteğe bağlı olarak, ortam değişkenini [`JULIA_PROFILE_PEEK_HEAP_SNAPSHOT`](@ref JULIA_PROFILE_PEEK_HEAP_SNAPSHOT) değerini `1` olarak ayarlayın, böylece otomatik olarak [heap snapshot](@ref Heap-Snapshots) toplayabilirsiniz.

```julia-repl
julia> foo()
##== the user sends a trigger while foo is running ==##
load: 2.53  cmd: julia 88903 running 6.16u 0.97s

======================================================================================
Information request received. A stacktrace will print followed by a 1.0 second profile
======================================================================================

signal (29): Information request: 29
__psynch_cvwait at /usr/lib/system/libsystem_kernel.dylib (unknown line)
_pthread_cond_wait at /usr/lib/system/libsystem_pthread.dylib (unknown line)
...

======================================================================
Profile collected. A report will print if the Profile module is loaded
======================================================================

Overhead ╎ [+additional indent] Count File:Line; Function
=========================================================
Thread 1 Task 0x000000011687c010 Total snapshots: 572. Utilization: 100%
   ╎147 @Base/client.jl:506; _start()
       ╎ 147 @Base/client.jl:318; exec_options(opts::Base.JLOptions)
...

Thread 2 Task 0x0000000116960010 Total snapshots: 572. Utilization: 0%
   ╎572 @Base/task.jl:587; task_done_hook(t::Task)
      ╎ 572 @Base/task.jl:879; wait()
...
```

### Customization

Profiling süresini [`Profile.set_peek_duration`](@ref) aracılığıyla ayarlayabilirsiniz.

Profil raporu, iş parçacığı ve görev bazında ayrılmıştır. Bunu geçersiz kılmak için `Profile.peek_report[]`'a argüman almayan bir fonksiyon geçirin. Yani, gruplamayı kaldırmak için `Profile.peek_report[] = () -> Profile.print()` kullanın. Bu, harici bir profil veri tüketicisi tarafından da geçersiz kılınabilir.

## Reference

```@docs
Profile.@profile
```

`Profile` içindeki yöntemler dışa aktarılmamış ve `Profile.print()` gibi çağrılması gerekiyor.

```@docs
Profile.clear
Profile.print
Profile.init
Profile.fetch
Profile.retrieve
Profile.callers
Profile.clear_malloc_data
Profile.get_peek_duration
Profile.set_peek_duration
```

## Memory profiling

```@docs
Profile.Allocs.@profile
```

`Profile.Allocs` içindeki yöntemler dışa aktarılmamıştır ve `Profile.Allocs.fetch()` gibi çağrılması gerekmektedir.

```@docs
Profile.Allocs.clear
Profile.Allocs.print
Profile.Allocs.fetch
Profile.Allocs.start
Profile.Allocs.stop
```

## Heap Snapshots

```@docs
Profile.take_heap_snapshot
```

`Profile` içindeki yöntemler dışa aktarılmamıştır ve `Profile.take_heap_snapshot()` gibi çağrılmalıdır.

```julia-repl
julia> using Profile

julia> Profile.take_heap_snapshot("snapshot.heapsnapshot")
```

Yığın üzerindeki julia nesnelerini izler ve kaydeder. Bu yalnızca Julia çöp toplayıcısı tarafından bilinen nesneleri kaydeder. Çöp toplayıcı tarafından yönetilmeyen dış kütüphaneler tarafından tahsis edilen bellek anlık görüntüde görünmeyecektir.

Yığın anlık görüntüsünü kaydederken OOM hatasından kaçınmak için, yığın anlık görüntüsünü dört dosyaya akıtarak akış seçeneği ekledik,

```julia-repl
julia> using Profile

julia> Profile.take_heap_snapshot("snapshot"; streaming=true)
```

"snapshot" dosyası, oluşturulan dosyalar için ön ek olarak kullanılır.

Oluşturulan anlık görüntü dosyaları, aşağıdaki komutla çevrimdışı olarak birleştirilebilir:

```julia-repl
julia> using Profile

julia> Profile.HeapSnapshot.assemble_snapshot("snapshot", "snapshot.heapsnapshot")
```

Oluşan yığın anlık görüntü dosyası, görüntülenmek üzere chrome geliştirici araçlarına yüklenebilir. Daha fazla bilgi için [chrome devtools docs](https://developer.chrome.com/docs/devtools/memory-problems/heap-snapshots/#view_snapshots) adresine bakın. Chromium yığın anlık görüntülerini analiz etmek için bir alternatif, VS Code uzantısı `ms-vscode.vscode-js-profile-flame`dir.

Firefox yığın anlık görüntüleri farklı bir formattadır ve Firefox şu anda Julia tarafından üretilen yığın anlık görüntülerini görüntülemek için *kullanılamaz*.
