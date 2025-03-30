# Environment Variables

Julia, bir dizi ortam değişkeni ile yapılandırılabilir; bu değişkenler, her işletim sistemi için alışıldık şekilde veya Julia içinden taşınabilir bir şekilde ayarlanabilir. Ortam değişkeni [`JULIA_EDITOR`](@ref JULIA_EDITOR) değerini `vim` olarak ayarlamak istediğinizi varsayalım, bu değişikliği durum bazında yapmak için `ENV["JULIA_EDITOR"] = "vim"` yazabilirsiniz (örneğin, REPL'de) veya aynı satırı kullanıcının ana dizinindeki `~/.julia/config/startup.jl` kullanıcı yapılandırma dosyasına ekleyerek kalıcı bir etki sağlarsınız. Aynı ortam değişkeninin mevcut değeri `ENV["JULIA_EDITOR"]` ifadesini değerlendirerek belirlenebilir.

Julia'nın genellikle kullandığı ortam değişkenleri `JULIA` ile başlar. Eğer [`InteractiveUtils.versioninfo`](@ref) `verbose=true` anahtar kelimesi ile çağrılırsa, çıktı, adlarında `JULIA` bulunanlar da dahil olmak üzere, Julia ile ilgili tanımlı ortam değişkenlerini listeleyecektir.

!!! note
    Çalışma zamanında, örneğin `~/.julia/config/startup.jl` içinde, ortam değişkenlerini değiştirmekten kaçınılması önerilir.

    Bir neden, bazı Julia dil değişkenlerinin, örneğin [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) ve [`JULIA_PROJECT`](@ref JULIA_PROJECT), Julia başlamadan önce ayarlanması gerektiğidir.

    Benzer şekilde, sysimage'deki kullanıcı modüllerinin `__init__()` fonksiyonları `startup.jl`'den önce çalıştırılır, bu nedenle bir `startup.jl`'de ortam değişkenlerini ayarlamak kullanıcı kodu için çok geç olabilir.

    Ayrıca, çalışma zamanında ortam değişkenlerini değiştirmek, aksi takdirde zararsız olan koda veri yarışları ekleyebilir.

    Bash'ta, ortam değişkenleri ya `export JULIA_NUM_THREADS=4` gibi bir komut çalıştırarak manuel olarak ayarlanabilir ya da aynı komutu `~/.bashrc` veya `~/.bash_profile` dosyasına ekleyerek Bash her başlatıldığında değişkenin ayarlanmasını sağlayabilirsiniz.


## File locations

### [`JULIA_BINDIR`](@id JULIA_BINDIR)

Julia yürütülebilir dosyasını içeren dizinin mutlak yolu, global değişken [`Sys.BINDIR`](@ref)'ı ayarlar. Eğer `$JULIA_BINDIR` ayarlanmamışsa, Julia çalışma zamanında `Sys.BINDIR` değerini belirler.

Yürütülebilir dosya, birinin içindedir.

```
$JULIA_BINDIR/julia
$JULIA_BINDIR/julia-debug
```

varsayılan olarak.

Küresel değişken `Base.DATAROOTDIR`, Julia ile ilişkili veri dizinine `Sys.BINDIR`'den bir göreceli yol belirler. Ardından yol

```
$JULIA_BINDIR/$DATAROOTDIR/julia/base
```

Julia'nın başlangıçta kaynak dosyalarını aradığı dizini belirler ( `Base.find_source_file()` aracılığıyla).

Benzer şekilde, global değişken `Base.SYSCONFDIR`, yapılandırma dosyası dizinine göre bir göreli yol belirler. Ardından Julia, bir `startup.jl` dosyasını arar.

```
$JULIA_BINDIR/$SYSCONFDIR/julia/startup.jl
$JULIA_BINDIR/../etc/julia/startup.jl
```

varsayılan olarak ( `Base.load_julia_startup()` aracılığıyla).

Örneğin, `/bin/julia` konumunda bir Julia çalıştırılabilir dosyası, `../share` olan bir `DATAROOTDIR` ve `../etc` olan bir `SYSCONFDIR` ile bir Linux kurulumu, `/bin` olarak ayarlanmış [`JULIA_BINDIR`](@ref JULIA_BINDIR) değerine sahip olacaktır, bir kaynak dosyası arama yolu olarak

```
/share/julia/base
```

ve ve global bir yapılandırma arama yolu

```
/etc/julia/startup.jl
```

### [`JULIA_PROJECT`](@id JULIA_PROJECT)

Bir dizin yolu, hangi projenin başlangıçta aktif proje olması gerektiğini belirtir. Bu ortam değişkenini ayarlamak, `--project` başlangıç seçeneğini belirtmekle aynı etkiye sahiptir, ancak `--project` daha yüksek önceliğe sahiptir. Değişken `@.` (sondaki noktaya dikkat edin) olarak ayarlandığında, Julia mevcut dizinden ve üst dizinlerinden `Project.toml` veya `JuliaProject.toml` dosyasını içeren bir proje dizini bulmaya çalışır. Ayrıca [Code Loading](@ref code-loading) bölümüne de bakın.

!!! note
    [`JULIA_PROJECT`](@ref JULIA_PROJECT) julia başlamadan önce tanımlanmalıdır; `startup.jl` dosyasında tanımlamak başlangıç sürecinde çok geçtir.


### [`JULIA_LOAD_PATH`](@id JULIA_LOAD_PATH)

[`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) ortam değişkeni, global Julia [`LOAD_PATH`](@ref) değişkenini doldurmak için kullanılır; bu değişken, hangi paketlerin `import` ve `using` ile yüklenebileceğini belirler (bkz. [Code Loading](@ref code-loading)).

[`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH)'in boş girişleri, `LOAD_PATH`'i doldururken varsayılan değeri olan `["@", "@v#.#", "@stdlib"]` ile genişletilir. Bu, `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448`'in zaten ayarlanıp ayarlanmadığına bakılmaksızın, yükleme yolu değerinin kabuk betiklerinde kolayca eklenmesine, önceliklendirilmesine vb. olanak tanır. Örneğin, `/foo/bar` dizinini `LOAD_PATH`'e eklemek için sadece şunu yapın:

```sh
export JULIA_LOAD_PATH="/foo/bar:$JULIA_LOAD_PATH"
```

Eğer [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) ortam değişkeni zaten ayarlandıysa, eski değeri `/foo/bar` ile önceliklendirilecektir. Öte yandan, eğer `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` ayarlanmamışsa, o zaman `/foo/bar:` olarak ayarlanacak ve bu da `LOAD_PATH` değerini `["/foo/bar", "@", "@v#.#", "@stdlib"]` olarak genişletecektir. Eğer `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` boş bir dizeye ayarlandıysa, boş bir `LOAD_PATH` dizisine genişler. Diğer bir deyişle, boş dize sıfır elemanlı bir dizi olarak yorumlanır, boş dizeden oluşan bir elemanlı dizi olarak değil. Bu davranış, ortam değişkeni aracılığıyla boş bir yük yolunun ayarlanabilmesi için seçilmiştir. Varsayılan yük yolunu istiyorsanız, ya ortam değişkenini kaldırın ya da bir değere sahip olması gerekiyorsa, onu `:` dizesine ayarlayın.

!!! note
    Windows'ta, yol öğeleri `;` karakteri ile ayrılır; bu, Windows'taki çoğu yol listesinde olduğu gibidir.


### [`JULIA_DEPOT_PATH`](@id JULIA_DEPOT_PATH)

[`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) ortam değişkeni, global Julia [`DEPOT_PATH`](@ref) değişkenini doldurmak için kullanılır; bu değişken, paket yöneticisinin yanı sıra Julia'nın kod yükleme mekanizmalarının, paket kayıtlarını, kurulu paketleri, adlandırılmış ortamları, depo kopyalarını, önbelleğe alınmış derlenmiş paket görüntülerini, yapılandırma dosyalarını ve REPL'nin geçmiş dosyasının varsayılan konumunu nerede arayacağını kontrol eder.

Shell `PATH` değişkeninden farklı olarak ancak [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) ile benzer şekilde, [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) içindeki boş girişlerin özel bir davranışı vardır:

  * Sonunda, kullanıcı deposunu *hariç tutarak* `DEPOT_PATH`'in varsayılan değerine genişletilir.
  * Başlangıçta, kullanıcı deposunu *içerecek şekilde* `DEPOT_PATH`'in varsayılan değerine genişletilir.

Bu, kullanıcı deposunun kolayca geçersiz kılınmasını sağlar, aynı zamanda Julia ile birlikte gelen kaynaklara, önbellek dosyaları, eserler vb. gibi erişimi korur. Örneğin, kullanıcı deposunu `/foo/bar` olarak değiştirmek için bir sonlandırıcı `:` kullanın.

```sh
export JULIA_DEPOT_PATH="/foo/bar:"
```

Tüm paket işlemleri, kayıtları klonlama veya paketleri yükleme gibi, artık `/foo/bar` dizinine yazacak, ancak boş giriş varsayılan sistem deposuna genişletildiğinden, herhangi bir paketlenmiş kaynak hala mevcut olacaktır. Gerçekten sadece `/foo/bar` deposunu kullanmak istiyorsanız ve herhangi bir paketlenmiş kaynağı yüklemek istemiyorsanız, ortam değişkenini sonundaki iki nokta olmadan `/foo/bar` olarak ayarlayın.

Tamamlayıcı varsayılan listeye, varsayılan kullanıcı deposunu da içerecek şekilde bir depo eklemek için, başına `:` koyun.

```sh
export JULIA_DEPOT_PATH=":/foo/bar"
```

Yukarıdaki kurala iki istisna vardır. İlk olarak, [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) boş bir dize olarak ayarlandığında, boş bir `DEPOT_PATH` dizisine genişler. Diğer bir deyişle, boş dize sıfır elemanlı bir dizi olarak yorumlanır, boş dizeden oluşan bir elemanlı dizi olarak değil. Bu davranış, bir ortam değişkeni aracılığıyla boş bir depo yolu ayarlamanın mümkün olabilmesi için seçilmiştir.

İkincisi, [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) içinde hiçbir kullanıcı deposu belirtilmemişse, boş giriş varsayılan depoya *kullanıcı deposunu da dahil ederek* genişletilir. Bu, ortam değişkeni ayarlanmamış gibi varsayılan depoyu kullanmayı, onu `:` dizesine ayarlayarak mümkün kılar.

!!! note
    Windows'ta, yol öğeleri `;` karakteri ile ayrılır; bu, Windows'taki çoğu yol listesi için de geçerlidir.


!!! note
    [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) julia başlamadan önce tanımlanmalıdır; bunu `startup.jl` dosyasında tanımlamak başlangıç sürecinde çok geçtir; bu noktada, ortam değişkeninden doldurulan `DEPOT_PATH` dizisini doğrudan değiştirebilirsiniz.


### [`JULIA_HISTORY`](@id JULIA_HISTORY)

REPL'nin geçmiş dosyasının mutlak yolu `REPL.find_hist_file()`. Eğer `$JULIA_HISTORY` ayarlanmamışsa, `REPL.find_hist_file()` varsayılan olarak

```
$(DEPOT_PATH[1])/logs/repl_history.jl
```

### [`JULIA_MAX_NUM_PRECOMPILE_FILES`](@id JULIA_MAX_NUM_PRECOMPILE_FILES)

Tek bir paketin ön derleme önbelleğinde saklanacak farklı örneklerinin maksimum sayısını ayarlar (varsayılan = 10).

### [`JULIA_VERBOSE_LINKING`](@id JULIA_VERBOSE_LINKING)

Eğer true olarak ayarlandıysa, ön derleme sırasında bağlayıcı komutları görüntülenecektir.

## Pkg.jl

### [`JULIA_CI`](@id JULIA_CI)

Eğer `true` olarak ayarlandıysa, bu, paket sunucusuna herhangi bir paket işleminin paket kullanım istatistiklerini toplama amacıyla sürekli entegrasyon (CI) sisteminin bir parçası olduğunu gösterir.

### [`JULIA_NUM_PRECOMPILE_TASKS`](@id JULIA_NUM_PRECOMPILE_TASKS)

Paketleri önceden derlerken kullanılacak paralel görev sayısı. [`Pkg.precompile`](https://pkgdocs.julialang.org/v1/api/#Pkg.precompile) adresine bakın.

### [`JULIA_PKG_DEVDIR`](@id JULIA_PKG_DEVDIR)

[`Pkg.develop`](https://pkgdocs.julialang.org/v1/api/#Pkg.develop) için paketleri indirmek üzere kullanılan varsayılan dizin.

### [`JULIA_PKG_IGNORE_HASHES`](@id JULIA_PKG_IGNORE_HASHES)

Eğer `1` olarak ayarlanırsa, bu, artefaktlardaki yanlış hash'leri yok sayacaktır. Bu dikkatli bir şekilde kullanılmalıdır, çünkü indirmelerin doğrulanmasını devre dışı bırakır, ancak dosyaları farklı dosya sistemleri arasında taşırken sorunları çözebilir. Daha fazla bilgi için [Pkg.jl issue #2317](https://github.com/JuliaLang/Pkg.jl/issues/2317) adresine bakın.

!!! compat "Julia 1.6"
    Bu yalnızca Julia 1.6 ve üzeri sürümlerde desteklenmektedir.


### [`JULIA_PKG_OFFLINE`](@id JULIA_PKG_OFFLINE)

Eğer `true` olarak ayarlanırsa, bu çevrimdışı modu etkinleştirecektir: bkz. [`Pkg.offline`](https://pkgdocs.julialang.org/v1/api/#Pkg.offline).

!!! compat "Julia 1.5"
    Pkg'nin çevrimdışı modu, Julia 1.5 veya daha yenisini gerektirir.


### [`JULIA_PKG_PRECOMPILE_AUTO`](@id JULIA_PKG_PRECOMPILE_AUTO)

Eğer `0` olarak ayarlanırsa, bu, manifestoyu değiştiren paket eylemleri tarafından otomatik ön derlemenin devre dışı bırakılmasını sağlar. Bakınız [`Pkg.precompile`](https://pkgdocs.julialang.org/v1/api/#Pkg.precompile).

### [`JULIA_PKG_SERVER`](@id JULIA_PKG_SERVER)

Paket kayıt defterinin kullanılacak URL'sini belirtir. Varsayılan olarak, `Pkg` Julia paketlerini almak için `https://pkg.julialang.org` kullanır. Ayrıca, PkgServer protokolünün kullanımını devre dışı bırakabilir ve bunun yerine paketlere doğrudan ev sahiplerinden (GitHub, GitLab, vb.) erişmek için şunu ayarlayabilirsiniz: `export JULIA_PKG_SERVER=""`

### [`JULIA_PKG_SERVER_REGISTRY_PREFERENCE`](@id JULIA_PKG_SERVER_REGISTRY_PREFERENCE)

Tercih edilen kayıt defteri türünü belirtir. Şu anda desteklenen değerler `conservative` (varsayılan), yalnızca depolama sunucusu tarafından işlenmiş kaynakları yayınlayacak (ve böylece PkgServers'dan mevcut olma olasılığı daha yüksek olacaktır), `eager` ise kaynaklarının mutlaka depolama sunucuları tarafından işlenmediği kayıt defterlerini yayınlayacaktır. Rastgele sunuculardan indirmeye izin vermeyen kısıtlayıcı güvenlik duvarlarının arkasındaki kullanıcılar `eager` türünü kullanmamalıdır.

!!! compat "Julia 1.7"
    Bu yalnızca Julia 1.7 ve üzerini etkiler.


### [`JULIA_PKG_UNPACK_REGISTRY`](@id JULIA_PKG_UNPACK_REGISTRY)

Eğer `true` olarak ayarlanırsa, bu kayıt defterini sıkıştırılmış tarball olarak depolamak yerine açacaktır.

!!! compat "Julia 1.7"
    Bu yalnızca Julia 1.7 ve üzerini etkiler. Daha önceki sürümler her zaman kayıt defterini açar.


### [`JULIA_PKG_USE_CLI_GIT`](@id JULIA_PKG_USE_CLI_GIT)

Eğer `true` olarak ayarlanırsa, git protokolünü kullanan Pkg işlemleri varsayılan libgit2 kütüphanesi yerine harici bir `git` yürütülebilir dosyası kullanacaktır.

!!! compat "Julia 1.7"
    `git` yürütülebilir dosyasının kullanımı yalnızca Julia 1.7 ve üzeri sürümlerde desteklenmektedir.


### [`JULIA_PKGRESOLVE_ACCURACY`](@id JULIA_PKGRESOLVE_ACCURACY)

Paket çözücüsünün doğruluğu. Bu pozitif bir tam sayı olmalıdır, varsayılan `1`'dir.

### [`JULIA_PKG_PRESERVE_TIERED_INSTALLED`](@id JULIA_PKG_PRESERVE_TIERED_INSTALLED)

Varsayılan paket yükleme stratejisini `Pkg.PRESERVE_TIERED_INSTALLED` olarak değiştirin, böylece paket yöneticisi, mümkün olduğunca fazla yüklü paket sürümünü koruyarak paketlerin sürümlerini yüklemeye çalışsın.

!!! compat "Julia 1.9"
    Bu yalnızca Julia 1.9 ve üzerini etkiler.


## Network transport

### [`JULIA_NO_VERIFY_HOSTS`](@id JULIA_NO_VERIFY_HOSTS)

### [`JULIA_SSL_NO_VERIFY_HOSTS`](@id JULIA_SSL_NO_VERIFY_HOSTS)

### [`JULIA_SSH_NO_VERIFY_HOSTS`](@id JULIA_SSH_NO_VERIFY_HOSTS)

### [`JULIA_ALWAYS_VERIFY_HOSTS`](@id JULIA_ALWAYS_VERIFY_HOSTS)

Belirli taşıma katmanları için kimlik doğrulaması yapılması gereken veya yapılmaması gereken ana bilgisayarları belirtin. [`NetworkOptions.verify_host`](https://github.com/JuliaLang/NetworkOptions.jl#verify_host)

### [`JULIA_SSL_CA_ROOTS_PATH`](@id JULIA_SSL_CA_ROOTS_PATH)

Belirtilen dosya veya dizin, sertifika otoritesi köklerini içermelidir. [`NetworkOptions.ca_roots`](https://github.com/JuliaLang/NetworkOptions.jl#ca_roots)

## External applications

### [`JULIA_SHELL`](@id JULIA_SHELL)

Julia'nın dış komutları çalıştırmak için kullanacağı shell'in mutlak yolu ( `Base.repl_cmd()` aracılığıyla). Varsayılan olarak `$SHELL` ortam değişkenine ayarlanmıştır ve `$SHELL` ayarlanmamışsa `/bin/sh`'ye geri döner.

!!! note
    Windows'ta bu ortam değişkeni göz ardı edilir ve harici komutlar doğrudan yürütülür.


### [`JULIA_EDITOR`](@id JULIA_EDITOR)

`InteractiveUtils.editor()` tarafından döndürülen editör ve örneğin [`InteractiveUtils.edit`](@ref)'da kullanılan, tercih edilen editörün komutunu ifade eder, örneğin `vim`.

`$JULIA_EDITOR` önceliğe sahiptir `$VISUAL`, bu da `$EDITOR`'a öncelik verir. Eğer bu ortam değişkenlerinden hiçbiri ayarlanmamışsa, o zaman editör Windows ve OS X'te `open` olarak alınır, ya da `/etc/alternatives/editor` mevcutsa, ya da aksi takdirde `emacs` olarak alınır.

Windows'ta Visual Studio Code'u kullanmak için `$JULIA_EDITOR`'ı `code.cmd` olarak ayarlayın.

## Parallelization

### [`JULIA_CPU_THREADS`](@id JULIA_CPU_THREADS)

Küresel değişkeni [`Base.Sys.CPU_THREADS`](@ref) geçersiz kılar, mevcut olan mantıksal CPU çekirdeklerinin sayısını.

### [`JULIA_WORKER_TIMEOUT`](@id JULIA_WORKER_TIMEOUT)

Bir [`Float64`](@ref) değeri ayarlayan `Distributed.worker_timeout()` (varsayılan: `60.0`) fonksiyonu, bir işçi sürecinin bir ana süreçle bağlantı kurmasını bekleyeceği süreyi (saniye cinsinden) belirler.

### [`JULIA_NUM_THREADS`](@id JULIA_NUM_THREADS)

Bir işaretsiz 64-bit tam sayı (`uint64_t`), Julia'ya mevcut olan maksimum iş parçacığı sayısını ayarlar. Eğer `$JULIA_NUM_THREADS` pozitif değilse veya ayarlanmamışsa, ya da CPU iş parçacığı sayısı sistem çağrılarıyla belirlenemiyorsa, iş parçacığı sayısı `1` olarak ayarlanır.

Eğer `$JULIA_NUM_THREADS` `auto` olarak ayarlandıysa, o zaman iş parçacığı sayısı CPU iş parçacığı sayısına ayarlanacaktır.

!!! note
    `JULIA_NUM_THREADS` julia'yı başlatmadan önce tanımlanmalıdır; `startup.jl` içinde tanımlamak, başlangıç sürecinde çok geçtir.


!!! compat "Julia 1.5"
    Julia 1.5 ve üzerindeki sürümlerde, başlatma sırasında `-t`/`--threads` komut satırı argümanı kullanılarak iş parçacığı sayısı da belirtilebilir.


!!! compat "Julia 1.7"
    `$JULIA_NUM_THREADS` için `auto` değeri Julia 1.7 veya üzerini gerektirir.


### [`JULIA_THREAD_SLEEP_THRESHOLD`](@id JULIA_THREAD_SLEEP_THRESHOLD)

Eğer `"infinite"` alt dizesi ile başlayan bir dizeye ayarlandıysa, dönen iş parçacıkları asla uyumaz. Aksi takdirde, `$JULIA_THREAD_SLEEP_THRESHOLD` bir işaretsiz 64-bit tam sayı (`uint64_t`) olarak yorumlanır ve dönen iş parçacıklarının uyuması gereken süreyi, nanosecond cinsinden, verir.

### [`JULIA_NUM_GC_THREADS`](@id JULIA_NUM_GC_THREADS)

Çöp Toplama tarafından kullanılan iş parçacığı sayısını ayarlar. Belirtilmemişse, işçi iş parçacıklarının sayısının yarısına ayarlanır.

!!! compat "Julia 1.10"
    Çevre değişkeni 1.10'da eklendi.


### [`JULIA_IMAGE_THREADS`](@id JULIA_IMAGE_THREADS)

Bir imaj derlemesi için bu Julia sürecinde kullanılan iş parçacığı sayısını belirleyen işaretsiz 32 bit tamsayı. Bu değişkenin değeri, modül küçük bir modülse göz ardı edilebilir. Belirtilmezse, [`JULIA_CPU_THREADS`](@ref JULIA_CPU_THREADS) değerinin veya mantıksal CPU çekirdeklerinin sayısının yarısının daha küçük olanı kullanılır.

### [`JULIA_IMAGE_TIMINGS`](@id JULIA_IMAGE_TIMINGS)

Görüntü derleme sırasında ayrıntılı zamanlama bilgilerinin yazdırılıp yazdırılmayacağını belirleyen bir boolean değeri. Varsayılan değeri 0'dır.

### [`JULIA_EXCLUSIVE`](@id JULIA_EXCLUSIVE)

Eğer `0` dışında bir değere ayarlandıysa, o zaman Julia'nın iş parçacığı politikası, özel bir makinede çalışmakla tutarlıdır: ana iş parçacığı proc 0 üzerindedir ve iş parçacıkları ilişkilendirilmiştir. Aksi takdirde, Julia işletim sisteminin iş parçacığı politikasını yönetmesine izin verir.

## REPL formatting

Çevre değişkenleri, REPL çıktısının terminalde nasıl biçimlendirileceğini belirler. Genel olarak, bu değişkenler [ANSI terminal escape sequences](https://en.wikipedia.org/wiki/ANSI_escape_code) olarak ayarlanmalıdır. Julia, aynı işlevselliğin çoğunu sunan yüksek seviyeli bir arayüz sağlar; [The Julia REPL](@ref) bölümüne bakın.

### [`JULIA_ERROR_COLOR`](@id JULIA_ERROR_COLOR)

`Base.error_color()` (varsayılan: açık kırmızı, `"\033[91m"`) hataların terminalde sahip olması gereken format.

### [`JULIA_WARN_COLOR`](@id JULIA_WARN_COLOR)

Uyarıların terminalde sahip olması gereken biçimlendirme `Base.warn_color()` (varsayılan: sarı, `"\033[93m"`).

### [`JULIA_INFO_COLOR`](@id JULIA_INFO_COLOR)

`Base.info_color()` (varsayılan: cyan, `"\033[36m"`) bilginin terminalde sahip olması gereken format.

### [`JULIA_INPUT_COLOR`](@id JULIA_INPUT_COLOR)

`Base.input_color()` (varsayılan: normal, `"\033[0m"`) terminalde girişi olması gereken biçimlendirme.

### [`JULIA_ANSWER_COLOR`](@id JULIA_ANSWER_COLOR)

`Base.answer_color()` (varsayılan: normal, `"\033[0m"`) terminalde çıkışın sahip olması gereken format.

## System and Package Image Building

### [`JULIA_CPU_TARGET`](@id JULIA_CPU_TARGET)

Hedef makine mimarisini (ön) derleme için [system](@ref sysimg-multi-versioning) ve [package images](@ref pkgimgs-multi-versioning) olarak değiştirin. `JULIA_CPU_TARGET` yalnızca bir disk önbelleğine çıkış olarak üretilen makine kodu görüntülemesini etkiler. `--cpu-target` veya `-C` ile karşılaştırıldığında, [command line option](@ref cli) yalnızca bir Julia oturumu içinde makine kodu yalnızca bellekte saklandığı için anında (JIT) kod üretimini etkilemez.

[`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) için geçerli değerler `julia -C help` komutunu çalıştırarak elde edilebilir.

[`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) ayğıtları farklı tür veya özelliklere sahip işlemcilerin bulunabileceği heterojen hesaplama sistemleri için önemlidir. Bu, bileşen düğümlerinin farklı işlemciler kullanabileceği yüksek performanslı hesaplama (HPC) kümelerinde yaygın olarak karşılaşılır.

CPU hedef dizesi, `;` ile ayrılmış dize listesidir; her dize bir CPU veya mimari adı ile başlar ve ardından `,` ile ayrılmış isteğe bağlı bir özellik listesi gelir. `generic` veya boş bir CPU adı, hedef ISA'nın temel gereksinim özellik setini ifade eder; bu, C/C++ çalışma zamanının derlendiği mimariden en azıdır. Her dize LLVM tarafından yorumlanır.

Birkaç özel özellik desteklenmektedir:

1. `clone_all`

    Bu, hedefin sysimg'deki tüm işlevleri klonlamasını zorlar. Negatif formda kullanıldığında (yani `-clone_all`), bu, belirli hedefler için varsayılan olarak etkin olan tam klonlamayı devre dışı bırakır.
2. `taban([0-9]*)`

    Bu, (0-tabanlı) temel hedef indeksini belirtir. Temel hedef, mevcut hedefin dayandığı hedeftir; yani, kopyalanmayan işlevler temel hedefteki sürümü kullanacaktır. Bu seçenek, temel hedef varsayılan hedef (0) değilse, temel hedefin tamamen kopyalanmasına neden olur (sanki `clone_all` onun için belirtilmiş gibi). İndeks yalnızca mevcut indeksten daha küçük olabilir.
3. `opt_size`

    Boyut için optimize edin, minimum performans etkisi ile. Clang/GCC'nin `-Os`.
4. `min_size`

    Boyut için yalnızca optimize et. Clang'ın `-Oz`.

## Debugging and profiling

### [`JULIA_DEBUG`](@id JULIA_DEBUG)

Dosya veya modül için hata ayıklama kaydını etkinleştirin, daha fazla bilgi için [`Logging`](@ref man-logging)'e bakın.

### [`JULIA_PROFILE_PEEK_HEAP_SNAPSHOT`](@id JULIA_PROFILE_PEEK_HEAP_SNAPSHOT)

Yürütme sırasında profil alma peek mekanizması aracılığıyla bir yığın anlık görüntüsü toplama özelliğini etkinleştirin. [Triggered During Execution](@ref)'ya bakın.

### [`JULIA_TIMING_SUBSYSTEMS`](@id JULIA_TIMING_SUBSYSTEMS)

Belirli bir Julia çalışması için bölgeleri etkinleştirmenizi veya devre dışı bırakmanızı sağlar. Örneğin, değişkeni `+GC,-INFERENCE` olarak ayarlamak, `GC` bölgelerini etkinleştirir ve `INFERENCE` bölgelerini devre dışı bırakır. [Dynamically Enabling and Disabling Zones](@ref)'ya bakın.

### [`JULIA_GC_ALLOC_POOL`](@id JULIA_GC_ALLOC_POOL)

### [`JULIA_GC_ALLOC_OTHER`](@id JULIA_GC_ALLOC_OTHER)

### [`JULIA_GC_ALLOC_PRINT`](@id JULIA_GC_ALLOC_PRINT)

Eğer ayarlanmışsa, bu ortam değişkenleri, isteğe bağlı olarak `'r'` karakteriyle başlayan ve ardından üç adet imzalı 64-bit tam sayının (`int64_t`) iki nokta ile ayrılmış bir dize interpolasyonu içeren dizeleri alır. Bu üçlü tam sayı `a:b:c`, aritmetik diziyi temsil eder: `a`, `a + b`, `a + 2*b`, ... `c`.

  * Eğer `jl_gc_pool_alloc()` fonksiyonu `n`'inci kez çağrılıyorsa ve `n`, `$JULIA_GC_ALLOC_POOL` ile temsil edilen aritmetik dizinin bir elemanıyse, o zaman çöp toplama zorlanır.
  * Eğer `maybe_collect()` fonksiyonu `n`'inci kez çağrılıyorsa ve `n`, `$JULIA_GC_ALLOC_OTHER` ile temsil edilen aritmetik dizinin bir elemanına ait ise, çöp toplama zorlanır.
  * Eğer `jl_gc_collect()` fonksiyonu `n`'inci kez çağrılıyorsa ve `n`, `$JULIA_GC_ALLOC_PRINT` ile temsil edilen aritmetik dizinin bir elemanıyse, o zaman `jl_gc_pool_alloc()` ve `maybe_collect()` çağrılarının sayıları yazdırılır.

Eğer ortam değişkeninin değeri `'r'` karakteriyle başlıyorsa, çöp toplama olayları arasındaki aralık rastgeleleştirilir.

!!! note
    Bu ortam değişkenleri yalnızca Julia'nın çöp toplama hata ayıklama ile derlenmiş olması durumunda etki eder (yani, `WITH_GC_DEBUG_ENV` yapılandırma dosyasında `1` olarak ayarlanmışsa).


### [`JULIA_GC_NO_GENERATIONAL`](@id JULIA_GC_NO_GENERATIONAL)

Eğer `0` dışında bir değere ayarlanırsa, Julia çöp toplayıcısı asla bellek üzerinde "hızlı süpürmeler" gerçekleştirmez.

!!! note
    Bu ortam değişkeninin yalnızca Julia'nın çöp toplama hata ayıklama ile derlenmesi durumunda bir etkisi vardır (yani, yapılandırma dosyasında `WITH_GC_DEBUG_ENV` değeri `1` olarak ayarlanmışsa).


### [`JULIA_GC_WAIT_FOR_DEBUGGER`](@id JULIA_GC_WAIT_FOR_DEBUGGER)

Eğer `0` dışında bir değere ayarlanırsa, Julia çöp toplayıcısı kritik bir hata meydana geldiğinde abort etmek yerine bir hata ayıklayıcının bağlanmasını bekleyecektir.

!!! note
    Bu ortam değişkeninin yalnızca Julia'nın çöp toplama hata ayıklama ile derlenmesi durumunda bir etkisi vardır (yani, yapılandırma dosyasında `WITH_GC_DEBUG_ENV` değeri `1` olarak ayarlanmışsa).


### [`ENABLE_JITPROFILING`](@id ENABLE_JITPROFILING)

Eğer `0` dışında bir şeye ayarlandıysa, derleyici anlık (JIT) profil oluşturma için bir olay dinleyicisi oluşturacak ve kaydedecektir.

!!! note
    Bu ortam değişkeninin yalnızca Julia'nın JIT profil oluşturma desteği ile derlenmesi durumunda bir etkisi vardır, ya da kullanarak

      * Intel'in [VTune™ Amplifier](https://software.intel.com/en-us/vtune) (`USE_INTEL_JITEVENTS` yapı yapılandırmasında `1` olarak ayarlandığında), veya
      * [OProfile](https://oprofile.sourceforge.io/news/) (`USE_OPROFILE_JITEVENTS` yapılandırma dosyasında `1` olarak ayarlandı).
      * [Perf](https://perf.wiki.kernel.org) (`USE_PERF_JITEVENTS` yapılandırma ayarında `1` olarak ayarlandığında). Bu entegrasyon varsayılan olarak etkinleştirilmiştir.


### [`ENABLE_GDBLISTENER`](@id ENABLE_GDBLISTENER)

`0` dışında bir değere ayarlandığında, Julia kodunun sürüm derlemelerinde GDB kaydını etkinleştirir. Julia'nın hata ayıklama derlemelerinde bu her zaman etkindir. `-g 2` ile kullanılması önerilir.

### [`JULIA_LLVM_ARGS`](@id JULIA_LLVM_ARGS)

LLVM arka ucuna geçirilecek argümanlar.

### `JULIA_FALLBACK_REPL`

Fallback repl yerine REPL.jl'yi zorlar.
