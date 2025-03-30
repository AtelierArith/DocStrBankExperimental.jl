```
WorkerConfig
```

[`ClusterManager`](@ref) tarafından kümelerine eklenen işçileri kontrol etmek için kullanılan tür. Tüm küme yöneticileri tarafından bir ana makineye erişmek için kullanılan bazı alanlar:

  * `io` – işçiye erişmek için kullanılan bağlantı (bir `IO` alt türü veya `Nothing`)
  * `host` – ana makine adresi (ya bir `String` ya da `Nothing`)
  * `port` – işçiye bağlanmak için ana makinedeki port (ya bir `Int` ya da `Nothing`)

Bazıları, zaten başlatılmış bir ana makineye işçi eklemek için küme yöneticisi tarafından kullanılır:

  * `count` – ana makinede başlatılacak işçi sayısı
  * `exename` – ana makinedeki Julia yürütülebilir dosyasının yolu, varsayılan olarak `"$(Sys.BINDIR)/julia"` veya `"$(Sys.BINDIR)/julia-debug"`
  * `exeflags` – Julia'yı uzaktan başlatırken kullanılacak bayraklar

`userdata` alanı, dış yöneticiler tarafından her işçi için bilgi depolamak için kullanılır.

Bazı alanlar `SSHManager` ve benzeri yöneticiler tarafından kullanılır:

  * `tunnel` – `true` (tünelleme kullan), `false` (tünelleme kullanma) veya [`nothing`](@ref) (yönetici için varsayılanı kullan)
  * `multiplex` – `true` (tünelleme için SSH çoklama kullan) veya `false`
  * `forward` – ssh'nin `-L` seçeneği için kullanılan yönlendirme seçeneği
  * `bind_addr` – uzaktaki ana makinede bağlanacak adres
  * `sshflags` – SSH bağlantısını kurarken kullanılacak bayraklar
  * `max_parallel` – ana makinede paralel olarak bağlanacak maksimum işçi sayısı

Bazı alanlar hem `LocalManager` hem de `SSHManager` tarafından kullanılır:

  * `connect_at` – bunun işçi-işçi veya sürücü-işçi kurulum çağrısı olup olmadığını belirler
  * `process` – bağlanacak işlem (genellikle yönetici bunu [`addprocs`](@ref) sırasında atar)
  * `ospid` – ana makine işletim sistemine göre işlem kimliği, işçi süreçlerini kesmek için kullanılır
  * `environ` – Local/SSH yöneticileri tarafından geçici bilgileri depolamak için kullanılan özel sözlük
  * `ident` – [`ClusterManager`](@ref) tarafından tanımlanan işçi
  * `connect_idents` – işçinin özel bir topoloji kullanıyorsa bağlanması gereken işçi kimlikleri listesi
  * `enable_threaded_blas` – işçilerde iş parçacıklı BLAS kullanılıp kullanılmayacağı, `true`, `false` veya `nothing`
