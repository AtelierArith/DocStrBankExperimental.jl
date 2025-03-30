# Reporting and analyzing crashes (segfaults)

Julia'yı kırmayı başardın. Tebrikler! Burada, bir şeyler ters gittiğinde karşılaşılan yaygın semptomlar için uygulayabileceğiniz bazı genel prosedürler toplanmıştır. Bu hata ayıklama adımlarından elde edilen bilgileri dahil etmek, bir segfault'u izlerken veya betiğinizin beklenenden daha yavaş çalışmasının nedenini anlamaya çalışırken bakım yapanlara büyük ölçüde yardımcı olabilir.

Eğer bu sayfaya yönlendirildiyseniz, yaşadığınız duruma en uygun semptomu bulun ve istenen hata ayıklama bilgilerini oluşturmak için talimatları izleyin. Semptomlar tablosu:

  * [Segfaults during bootstrap (`sysimg.jl`)](@ref)
  * [Segfaults when running a script](@ref)
  * [Errors during Julia startup](@ref)
  * [Other generic segfaults or unreachables reached](@ref)

## [Version/Environment info](@id dev-version-info)

Hata ne olursa olsun, hangi Julia sürümünü kullandığımızı her zaman bilmemiz gerekecek. Julia ilk başlatıldığında, bir sürüm numarası ve tarih ile birlikte bir başlık yazdırılır. Ayrıca, oluşturduğunuz herhangi bir raporda `versioninfo()` çıktısını (standart kütüphaneden [`InteractiveUtils`](@ref InteractiveUtils.versioninfo) olarak dışa aktarılmıştır) da eklemeyi unutmayın:

```@repl
using InteractiveUtils
versioninfo()
```

## Segfaults during bootstrap (`sysimg.jl`)

Segfaultlar, Julia'nın `base/` klasöründeki kod derleme sürecinin sonunda `make` işleminin bir belirtisi olarak yaygındır. Bu sürecin beklenmedik bir şekilde sona ermesine birçok faktör katkıda bulunabilir, ancak genellikle Julia'nın C kodu bölümündeki bir hatadan kaynaklanır ve bu nedenle genellikle `gdb` içinde bir hata ayıklama derlemesi ile hata ayıklanması gerekir. Açıkça:

Julia'nın bir hata ayıklama derlemesini oluşturun:

```
$ cd <julia_root>
$ make debug
```

Bu sürecin muhtemelen normal bir `make` komutuyla aynı hata ile başarısız olacağını unutmayın, ancak bu, `gdb`'ye doğru geri izlemeler almak için gereken hata ayıklama sembollerini sunan bir hata ayıklama yürütülebilir dosya oluşturacaktır. Sonra, `gdb` içinde bootstrap sürecini manuel olarak çalıştırın:

```
$ cd base/
$ gdb -x ../contrib/debug_bootstrap.gdb
```

Bu, `gdb`'yi başlatacak, Julia'nın hata ayıklama sürümünü kullanarak bootstrap sürecini çalıştırmaya çalışacak ve (ne zaman olursa olsun) bir segfault oluşursa bir geri izleme (backtrace) yazdıracaktır. Tam geri izlemeyi almak için birkaç kez `<enter>` tuşuna basmanız gerekebilir. Geri izleme ile birlikte [gist](https://gist.github.com) oluşturun, [version info](@ref dev-version-info) ve aklınıza gelebilecek diğer ilgili bilgileri ekleyin ve yeni bir [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen) açın ve giste bir bağlantı ekleyin.

## Segfaults when running a script

Prosedür, [Segfaults during bootstrap (`sysimg.jl`)](@ref) ile çok benzer. Julia'nın bir hata ayıklama derlemesini oluşturun ve scriptinizi hata ayıklanmış bir Julia süreci içinde çalıştırın:

```
$ cd <julia_root>
$ make debug
$ gdb --args usr/bin/julia-debug <path_to_your_script>
```

Not edin ki `gdb` burada, talimatlar bekliyor olacak. Süreci çalıştırmak için `r` yazın ve segfault oluştuğunda bir geri izleme oluşturmak için `bt` yazın:

```
(gdb) r
Starting program: /home/sabae/src/julia/usr/bin/julia-debug ./test.jl
...
(gdb) bt
```

Oluşturun bir [gist](https://gist.github.com) ile geri izleme, [version info](@ref dev-version-info) ve düşünebileceğiniz diğer ilgili bilgileri ve yeni bir [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen) açın Github'da bir bağlantı ile gist'e.

## Errors during Julia startup

Bazen Julia'nın başlatma sürecinde (özellikle ikili dağıtımlar kullanıldığında, kaynak koddan derlemek yerine) aşağıdaki gibi hatalar meydana gelir:

```julia
$ julia
exec: error -5
```

Bu hatalar genellikle bir şeyin önyükleme aşamasının çok erken bir aşamasında düzgün bir şekilde yüklenmediğini gösterir ve neyin yanlış gittiğini belirlemenin en iyi yolu, `julia` sürecinin disk etkinliğini denetlemek için harici araçlar kullanmaktır:

  * Linux'ta `strace` kullanın:

    ```
    $ strace julia
    ```
  * OSX'te `dtruss` kullanın:

    ```
    $ dtruss -f julia
    ```

Create a [gist](https://gist.github.com) with the `strace`/ `dtruss` output, the [version info](@ref dev-version-info), and any other pertinent information and open a new [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen) on Github with a link to the gist.

## Other generic segfaults or unreachables reached

Belirtilen diğer yerlerde, `julia`'nın `rr` ile izler oluşturma konusunda iyi bir entegrasyonu olduğu belirtilmiştir; bu, Linux'ta, bir çökme sonrası `julia`'yı otomatik olarak `rr` altında çalıştırma ve izleri paylaşma yeteneğini içerir. Bu, böyle çökme durumlarını hata ayıklarken son derece faydalı olabilir ve JuliaLang/julia deposuna çökme sorunları bildirilirken güçlü bir şekilde teşvik edilmektedir. `julia`'yı otomatik olarak `rr` altında çalıştırmak için:

```julia
julia --bug-report=rr
```

Yerel olarak `rr` izini oluşturmak, ancak paylaşmamak için şunları yapabilirsiniz:

```julia
julia --bug-report=rr-local
```

Not edin ki bu yalnızca Linux'ta çalışır. [Time Travelling Bug Reporting](https://julialang.org/blog/2020/05/rr/) üzerindeki blog yazısında daha fazla ayrıntı bulunmaktadır.

## Glossary

Bu kılavuzda kısayol olarak kullanılan birkaç terim bulunmaktadır:

  * `<julia_root>` Julia kaynak ağacının kök dizinini ifade eder; örneğin, `base`, `deps`, `src`, `test` gibi klasörler içermelidir.....
