```
addprocs(machines; tunnel=false, sshflags=``, max_parallel=10, kwargs...) -> Süreç tanımlayıcılarının listesi
```

Uzak makinelerde SSH üzerinden işçi süreçleri ekleyin. Yapılandırma, anahtar argümanlarla yapılır (aşağıya bakınız). Özellikle, `exename` anahtar kelimesi, uzak makine(ler)deki `julia` ikili dosyasının yolunu belirtmek için kullanılabilir.

`machines`, `[user@]host[:port] [bind_addr[:port]]` biçiminde verilen "makine spesifikasyonları" dizisidir. `user`, geçerli kullanıcıya ve `port` standart SSH portuna varsayılan olarak ayarlanır. Eğer `[bind_addr[:port]]` belirtilirse, diğer işçiler bu işçiye belirtilen `bind_addr` ve `port` üzerinden bağlanacaktır.

`machines` dizisinde bir demet kullanarak veya `(machine_spec, count)` biçiminde birden fazla süreci uzak bir ana bilgisayarda başlatmak mümkündür; burada `count`, belirtilen ana bilgisayarda başlatılacak işçi sayısını belirtir. İşçi sayısı olarak `:auto` geçmek, uzak ana bilgisayardaki CPU iş parçacığı sayısı kadar işçi başlatır.

**Örnekler**:

```julia
addprocs([
    "remote1",               # 'remote1' üzerinde geçerli kullanıcı adıyla bir işçi
    "user@remote2",          # 'user' kullanıcı adıyla 'remote2' üzerinde bir işçi
    "user@remote3:2222",     # 'remote3' için SSH portunu '2222' olarak belirtme
    ("user@remote4", 4),     # 'remote4' üzerinde 4 işçi başlat
    ("user@remote5", :auto), # 'remote5' üzerinde CPU iş parçacığı sayısı kadar işçi başlat
])
```

**Anahtar argümanlar**:

  * `tunnel`: `true` ise, ana süreçten işçiye bağlanmak için SSH tünellemesi kullanılacaktır. Varsayılan `false`'dır.
  * `multiplex`: `true` ise, SSH tünellemesi için SSH çoklama kullanılır. Varsayılan `false`'dır.
  * `ssh`: işçileri başlatmak için kullanılan SSH istemci yürütülebilir dosyasının adı veya yolu. Varsayılan `"ssh"`'dir.
  * `sshflags`: ek ssh seçeneklerini belirtir, örneğin ```sshflags=`-i /home/foo/bar.pem` ```
  * `max_parallel`: bir ana bilgisayara paralel olarak bağlanan maksimum işçi sayısını belirtir. Varsayılan 10'dur.
  * `shell`: işçilerin ssh ile bağlandığı kabuk türünü belirtir.

      * `shell=:posix`: POSIX uyumlu bir Unix/Linux kabuğu (sh, ksh, bash, dash, zsh, vb.). Varsayılan.
      * `shell=:csh`: Unix C kabuğu (csh, tcsh).
      * `shell=:wincmd`: Microsoft Windows `cmd.exe`.
  * `dir`: işçilerin çalışma dizinini belirtir. Varsayılan, ana bilgisayarın geçerli dizinidir ( `pwd()` ile bulunur).
  * `enable_threaded_blas`: `true` ise, eklenen süreçlerde BLAS çoklu iş parçacıklarında çalışacaktır. Varsayılan `false`'dır.
  * `exename`: `julia` yürütülebilir dosyasının adı. Varsayılan `"$(Sys.BINDIR)/julia"` veya `"$(Sys.BINDIR)/julia-debug"`'dır. Tüm uzak makinelerde ortak bir Julia sürümünün kullanılması önerilir, aksi takdirde serileştirme ve kod dağıtımı başarısız olabilir.
  * `exeflags`: işçi süreçlerine geçirilen ek bayraklar.
  * `topology`: İşçilerin birbirine nasıl bağlandığını belirtir. Bağlı olmayan işçiler arasında bir mesaj göndermek bir hataya neden olur.

      * `topology=:all_to_all`: Tüm süreçler birbirine bağlıdır. Varsayılan.
      * `topology=:master_worker`: Sadece sürücü süreci, yani `pid` 1 işçilere bağlanır. İşçiler birbirine bağlanmaz.
      * `topology=:custom`: Küme yöneticisinin `launch` yöntemi, `WorkerConfig` içindeki `ident` ve `connect_idents` alanları aracılığıyla bağlantı topolojisini belirtir. Bir küme yöneticisi kimliği `ident` olan bir işçi, `connect_idents` içinde belirtilen tüm işçilere bağlanacaktır.
  * `lazy`: Sadece `topology=:all_to_all` ile uygulanabilir. `true` ise, işçi-işçi bağlantıları tembel bir şekilde kurulur, yani işçiler arasında bir uzak çağrının ilk örneğinde kurulur. Varsayılan `true`'dur.
  * `env`: `env=["JULIA_DEPOT_PATH"=>"/depot"]` gibi dize çiftleri içeren bir dizi sağlayarak, çevre değişkenlerinin uzak makinede ayarlanmasını talep eder. Varsayılan olarak yalnızca `JULIA_WORKER_TIMEOUT` çevre değişkeni otomatik olarak yerel ortamdan uzak ortama geçirilir.
  * `cmdline_cookie`: kimlik doğrulama çerezini `--worker` komut satırı seçeneği aracılığıyla geçin. Çerezi ssh stdio aracılığıyla geçmenin (daha güvenli) varsayılan davranışı, daha eski (pre-ConPTY) Julia veya Windows sürümleri kullanan Windows işçileriyle takılabilir; bu durumda `cmdline_cookie=true` bir geçici çözüm sunar.

!!! compat "Julia 1.6"
    `ssh`, `shell`, `env` ve `cmdline_cookie` anahtar argümanları Julia 1.6'da eklendi.


Çevre değişkenleri:

Ana süreç, yeni başlatılan bir işçi ile 60.0 saniye içinde bağlantı kurmayı başaramazsa, işçi bunu ölümcül bir durum olarak değerlendirir ve sonlandırır. Bu zaman aşımı, `JULIA_WORKER_TIMEOUT` çevre değişkeni aracılığıyla kontrol edilebilir. Ana süreçteki `JULIA_WORKER_TIMEOUT` değeri, yeni başlatılan bir işçinin bağlantı kurulmasını beklediği saniye sayısını belirtir.
