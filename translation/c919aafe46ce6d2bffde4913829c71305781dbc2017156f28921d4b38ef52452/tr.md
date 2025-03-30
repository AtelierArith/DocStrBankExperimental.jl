# Binary distributions

Bu notlar, çeşitli platformlarda dağıtım için Julia'nın ikili dağıtımını derlemek isteyenler içindir. Julia'yı mümkün olduğunca geniş bir şekilde yaymak isteyen kullanıcıları seviyoruz, onu mümkün olan en geniş işletim sistemi ve donanım yapılandırmaları yelpazesinde denemelerini istiyoruz. Her platformun taşınabilir, çalışan bir Julia dağıtımı oluşturmak için izlenmesi gereken belirli zorlukları ve süreçleri olduğundan, notların çoğunu işletim sistemine göre ayırdık.

Not edin ki, Julia için kod [MIT-licensed, with a few exceptions](https://github.com/JuliaLang/julia/blob/master/LICENSE.md) iken, burada açıklanan tekniklerle oluşturulan dağıtım GPL lisanslı olacaktır, çünkü `SuiteSparse` gibi çeşitli bağımlı kütüphaneler GPL lisanslıdır. Gelecekte Julia'nın GPL olmayan bir dağıtımını elde etmeyi umuyoruz.

## Versioning and Git

Makefile, `VERSION` dosyasını ve git deposundaki commit hash'lerini ve etiketlerini kullanarak, splash ekranını doldurmak ve `versioninfo()` çıktısını oluşturmak için kullandığımız bilgileri içeren `base/version_git.jl` dosyasını oluşturur. Eğer bir nedenle git deposunun inşa sırasında mevcut olmasını istemiyorsanız, `base/version_git.jl` dosyasını önceden oluşturmalısınız:

```
make -C base version_git.jl.phony
```

Julia'nın, popüler paket yöneticileri tarafından henüz dahil edilmemiş yamanmış sürümleri kullandığı birçok derleme bağımlılığı vardır. Bu bağımlılıklar genellikle derleme sırasında otomatik olarak indirilir, ancak Julia'yı internet erişimi olmayan bir bilgisayarda derleyebilmek istiyorsanız, özel make hedefi ile tam kaynak dağıtım arşivi oluşturmalısınız.

```
make full-source-dist
```

julia-sürüm-commit.tar.gz arşivini gerekli tüm bağımlılıklarla birlikte oluşturur.

Tagged bir sürüm derlerken, splash ekranında dal/commit hash bilgilerini göstermiyoruz. 45 karaktere kadar bir sürüm açıklaması göstermek için bu satırı kullanabilirsiniz. Bu satırı ayarlamak için bir Make.user dosyası oluşturmalısınız:

```
override TAGGED_RELEASE_BANNER = "my-package-repository build"
```

## Target Architectures

Varsayılan olarak, Julia sistem görüntüsünü derleme makinesinin yerel mimarisine optimize eder. Bu genellikle paketler oluştururken istediğiniz şey değildir, çünkü bu, Julia'nın uyumsuz CPU'lara sahip herhangi bir makinede (özellikle daha kısıtlı komut setlerine sahip eski olanlarda) başlatılmasını engelleyecektir.

Bu nedenle, `make` çağrısı yaparken `MARCH` değişkenini geçmenizi öneririz ve bunu desteklemeyi düşündüğünüz temel hedefe ayarlarsınız. Bu, hem Julia yürütülebilir dosyası hem de kütüphaneler için hedef CPU'yu belirleyecek ve sistem görüntüsünü (sonuncusu ayrıca [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) kullanılarak ayarlanabilir). x86 CPU'lar için genellikle yararlı değerler `x86-64` ve `core2` (64 bit derlemeleri için) ve `pentium4` (32 bit derlemeleri için) dir. Ne yazık ki, Pentium 4'ten daha eski CPU'lar şu anda desteklenmemektedir (bkz. [this issue](https://github.com/JuliaLang/julia/issues/7185)).

LLVM tarafından desteklenen tüm CPU hedeflerinin tam listesi `llc -mattr=help` komutunu çalıştırarak elde edilebilir.

## Linux

Linux'te `make binary-dist`, tamamen işlevsel bir Julia kurulumu içeren bir tarball oluşturur. Eğer bir `.deb` veya `.rpm` gibi bir dağıtım paketi oluşturmak istiyorsanız, biraz ekstra çaba gereklidir. Debian ve Ubuntu tabanlı sistemler için `.deb` paketleri oluşturmak üzere gereken meta verilerin bir örneği için [julia-debian](https://github.com/staticfloat/julia-debian) deposuna bakın. RPM tabanlı dağıtımlar için [Fedora package](https://src.fedoraproject.org/rpms/julia) adresine bakın. Henüz denememiş olsak da, [Alien](https://wiki.debian.org/Alien) çeşitli Linux dağıtımları için Julia paketleri oluşturmak üzere kullanılabilir.

Julia, `make` ve `make install` çağırırken geçirebileceğiniz `prefix` ve diğer ortam değişkenleri aracılığıyla standart kurulum dizinlerini geçersiz kılmayı destekler. Bunların listesi için Make.inc dosyasına bakın. Ayrıca, kurulumu geçici bir dizine zorlamak için `DESTDIR` de kullanılabilir.

Varsayılan olarak, Julia `$prefix/etc/julia/startup.jl` dosyasını kurulum genelinde bir başlangıç dosyası olarak yükler. Bu dosya, dağıtım yöneticileri tarafından özel yollar veya başlangıç kodu ayarlamak için kullanılabilir. Linux dağıtım paketleri için, eğer `$prefix` `/usr` olarak ayarlandıysa, bakılacak bir `/usr/etc` yoktur. Bu, Julia'nın özel `etc` dizininin yolunun değiştirilmesini gerektirir. Bu, derleme sırasında `sysconfdir` make değişkeni aracılığıyla yapılabilir. Derleme sırasında `make` komutuna `sysconfdir=/etc` parametresini geçerek, Julia önce `/etc/julia/startup.jl` dosyasını kontrol edecek, ardından `$prefix/etc/julia/startup.jl` dosyasını deneyecektir.

## OS X

OSX'te ikili dağıtım oluşturmak için önce Julia'yı derleyin, ardından `contrib/mac/app` dizinine gidin ve Julia'nın düzgün bir şekilde derlenmesi sırasında kullanılan aynı makevars ile `make` komutunu çalıştırın. Bu, `contrib/mac/app` dizininde tamamen bağımsız bir Julia.app içeren bir `.dmg` dosyası oluşturacaktır.

Alternatif olarak, Julia, `make` komutunu `darwinframework` hedefi ile ve `DARWIN_FRAMEWORK=1` ayarı ile çağırarak bir çerçeve olarak oluşturulabilir. Örneğin, `make DARWIN_FRAMEWORK=1 darwinframework`.

## Windows

Windows üzerinde bir Julia dağıtımı oluşturma talimatları [build devdocs for Windows](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/windows.md) adresinde açıklanmaktadır.

## Notes on BLAS and LAPACK

Julia, varsayılan olarak OpenBLAS'ı inşa eder; bu, BLAS ve LAPACK kütüphanelerini içerir. 32-bit mimarilerde, Julia OpenBLAS'ı 32-bit tamsayılar kullanacak şekilde inşa ederken, 64-bit mimarilerde Julia OpenBLAS'ı 64-bit tamsayılar (ILP64) kullanacak şekilde inşa eder. BLAS ve LAPACK API rutinlerini çağıran tüm Julia fonksiyonlarının doğru genişlikte tamsayılar kullanması önemlidir.

Çoğu BLAS ve LAPACK dağıtımı, Linux dağıtımlarında sağlanır ve hatta ticari uygulamalar, 32-bit API'leri kullanan kütüphanelerle birlikte gelir. Birçok durumda, 64-bit API ayrı bir kütüphane olarak sağlanır.

Vendor tarafından sağlanan veya işletim sistemi tarafından sağlanan kütüphaneler kullanıldığında, Julia derlemesi sırasında `USE_BLAS64` adlı bir `make` seçeneği mevcuttur. `make USE_BLAS64=0` yapıldığında, Julia, tüm tam sayıların 32-bit genişliğinde olduğu varsayımıyla 32-bit API'sini dikkate alarak BLAS ve LAPACK'i çağıracaktır, bu durum 64-bit mimaride bile geçerlidir.

Diğer Julia'nın kullandığı kütüphaneler, SuiteSparse gibi, dahili olarak BLAS ve LAPACK kullanır. API'lerin, BLAS ve LAPACK'a bağımlı olan tüm kütüphaneler arasında tutarlı olması gerekir. Julia derleme süreci, bu kütüphanelerin hepsini doğru bir şekilde derleyecektir, ancak varsayılanları geçersiz kılarken ve sistem tarafından sağlanan kütüphaneleri kullanırken, bu tutarlılığın sağlanması gerekmektedir.

Ayrıca, Linux dağıtımlarının bazen birden fazla OpenBLAS sürümü sunduğunu, bunlardan bazılarının çoklu iş parçacığı desteği sağladığını ve diğerlerinin yalnızca seri modda çalıştığını unutmayın. Örneğin, Fedora'da `libopenblasp.so` çok iş parçacıklı, ancak `libopenblas.so` değildir. Optimal performans için ilkiyi kullanmanızı öneririz. Varsayılan `libopenblas.so`'dan farklı bir OpenBLAS kütüphanesi seçmek için `make` komutuna `LIBBLAS=-l$(YOURBLAS)` ve `LIBBLASNAME=lib$(YOURBLAS)` parametrelerini geçin, `$(YOURBLAS)` kısmını kütüphanenizin adıyla değiştirin. Ayrıca, paketinizin versiyonsuz `.so` symlink'ine ihtiyaç duymadan çalışmasını istiyorsanız, kütüphanenin adının sonuna `.so.0` ekleyebilirsiniz.

Sonunda, OpenBLAS kendi optimize edilmiş LAPACK sürümünü içerir. `USE_SYSTEM_BLAS=1` ve `USE_SYSTEM_LAPACK=1` ayarlarsanız, `LIBLAPACK=-l$(YOURBLAS)` ve `LIBLAPACKNAME=lib$(YOURBLAS)` ayarlarını da yapmalısınız. Aksi takdirde, referans LAPACK kullanılacak ve performans genellikle çok daha düşük olacaktır.

Julia 1.7'den itibaren, Julia [libblastrampoline](https://github.com/JuliaLinearAlgebra/libblastrampoline) kullanarak çalışma zamanında farklı bir BLAS seçer.

# Point releasing 101

Bir nokta/yama sürümü oluşturmak, birkaç farklı adımdan oluşur.

## Backporting commits

Bazı çekme istekleri "backport pending x.y" olarak etiketlenmiştir, örneğin "backport pending 0.6". Bu, release-x.y dalından etiketlenen bir sonraki sürümün, o çekme isteğindeki commit(ler)i içermesi gerektiğini belirtir. Çekme isteği master'a birleştirildikten sonra, her bir commit [cherry picked](https://git-scm.com/docs/git-cherry-pick) özel bir dala aktarılmalıdır ve bu dal nihayetinde release-x.y'ye birleştirilecektir.

### Creating a backports branch

Öncelikle, release-x.y temel alınarak yeni bir dal oluşturun. Julia dalları için tipik kural, dal adını kişisel bir dal olması durumunda baş harflerinizle ön eklemektir. Örnek olması açısından, dalın yazarının Jane Smith olduğunu varsayalım.

```
git fetch origin
git checkout release-x.y
git rebase origin/release-x.y
git checkout -b js/backport-x.y
```

Bu, yeni bir dal oluşturmadan önce yerel release-x.y kopyanızın origin ile güncel olmasını sağlar.

### Cherry picking commits

Şimdi gerçek geri taşıma işlemini yapıyoruz. GitHub web arayüzünde "backport pending x.y" etiketine sahip tüm birleştirilmiş çekme isteklerini bulun. Bunların her biri için, en alta gidin ve "someperson merged commit `123abc` into `master` XX minutes ago" yazan yeri bulun. Commit adının bir bağlantı olduğunu unutmayın; eğer tıklarsanız, commit'in içeriğini göreceksiniz. Eğer bu sayfa `123abc`'nin birleştirme commit'i olduğunu gösteriyorsa, PR sayfasına geri dönün - birleştirme commit'lerini istemiyoruz, gerçek commit'leri istiyoruz. Ancak, eğer bu birleştirme commit'i göstermiyorsa, bu, PR'nın squash-merge edildiği anlamına gelir. Bu durumda, bu sayfada listelenen commit'in yanındaki git SHA'sını kullanın.

Bir kez commit'in SHA'sını aldıktan sonra, onu geri alma dalına cherry-pick yapın:

```
git cherry-pick -x -e <sha>
```

Çatışmaların manuel olarak çözülmesi gerekebilir. Çatışmalar çözüldükten sonra (varsa), commit mesajının gövdesine commit'i tanıtan GitHub pull isteğine bir referans ekleyin.

Tüm ilgili commitler backports dalına eklendikten sonra, dalı GitHub'a gönderin.

## Checking for performance regressions

Point sürümleri asla performans gerilemeleri getirmemelidir. Neyse ki, Julia benchmark botu Nanosoldier, yalnızca master değil, herhangi bir dal üzerinde benchmark çalıştırabilir. Bu durumda, js/backport-x.y'nin benchmark sonuçlarını release-x.y ile kontrol etmek istiyoruz. Bunu yapmak için, backporting pull request'inizde bir yorum kullanarak Nanosoldier'ı robotik uykusundan uyandırın:

```markdown
@nanosoldier `runbenchmarks(ALL, vs=":release-x.y")`
```

Bu, release-x.y ve js/backport-x.y üzerindeki tüm kayıtlı kıyaslamaları çalıştıracak ve sonuçların bir özetini üretecek, tüm iyileştirmeleri ve gerilemeleri işaretleyecektir.

Eğer Nanosoldier herhangi bir gerileme bulursa, yerel olarak doğrulamayı deneyin ve gerekirse Nanosoldier'ı yeniden çalıştırın. Eğer gerilemeler gerçek olarak kabul ediliyorsa, bunu düzeltmek için mevcutsa master üzerinde bir commit bulmanız gerekecek, aksi takdirde gerilemeye neyin sebep olduğunu belirlemeli ve master'a bir yamanın (veya kodu bilen birinin yama göndermesini sağlamalısınız) gönderilmesini sağlamalısınız, ardından bu birleştirildikten sonra commit'i geri port etmelisiniz. (Ya da uygun ise doğrudan geri port dalına bir yama gönderebilirsiniz.)

## Building test binaries

`release-x.y` dalgaçına geri yükleme PR'ı birleştirildikten sonra, yerel Julia kopyanızı güncelleyin, ardından dalgaçın SHA'sını almak için

```
git rev-parse origin/release-x.y
```

Bunu elinizin altında bulundurun, çünkü bu, buildbot UI'sindeki "Revizyon" alanına gireceğiniz şeydir.

Şu anda, PackageEvaluator'ı çalıştırmak için kullanılan Linux x86-64 için ikili dosyalara ihtiyacınız var. https://buildog.julialang.org adresine gidin, `nuke_linux64` için bir iş gönderin, ardından SHA'yı revizyon olarak vererek `package_linux64` için bir iş sıraya alın. Paketleme işi tamamlandığında, ikili dosya AWS'deki `julialang2` kovasına yüklenecektir. URL'yi alın, çünkü bu PackageEvaluator için kullanılacaktır.

## Checking for package breakages

Nokta sürümleri paketleri asla bozmalıdır, kullanıcıya yönelik olmayan temel iç yapıları kullanarak ciddi şekilde sorgulanabilir hileler yapan paketler hariç. (Bu durumlarda, belki paket yazarıyla bir konuşma yapmalısınız.)

Gelecek yeni sürümde yapılan değişikliklerin paketleri bozup bozmayacağını kontrol etmek, genellikle "PkgEval" olarak kısaltılan [PackageEvaluator](https://github.com/JuliaCI/PackageEvaluator.jl) kullanılarak gerçekleştirilebilir. PkgEval, GitHub depolarındaki ve pkg.julialang.org'daki durum rozetlerini doldurur. Genellikle Nanosoldier'ın benchmarking dışı düğümlerinden birinde çalışır ve görevlerini ayrı, paralel VirtualBox sanal makinelerinde gerçekleştirmek için Vagrant kullanır.

### Setting up PackageEvaluator

Clone PackageEvaluator ve `backport-x.y.z` adında bir dal oluşturun ve onu kontrol edin. Gerekli değişikliklerin biraz karmaşık ve kafa karıştırıcı olduğunu unutmayın ve umarım bu, PackageEvaluator'ün gelecekteki bir sürümünde ele alınır. Yapılacak değişiklikler, [this commit](https://github.com/JuliaCI/PackageEvaluator.jl/commit/5ba6a3b000e7a3793391d16f695c8704b91d6016) model alınarak yapılacaktır.

Kurulum betiği, ilk argüman olarak çalıştırılacak Julia sürümünü ve ikinci argüman olarak paket adlarının aralığını alır (A-K için AK, L-Z için LZ). Temel fikir, bunu biraz değiştirerek yalnızca iki Julia sürümünü, mevcut x.y sürümünü ve geri port sürümümüzü çalıştırmak, her biri için üç paket aralığı ile çalışmaktır.

Bağlantılı farkta, ikinci argümanın LZ olması durumunda, geri yükleme dalımızdan oluşturulan ikili dosyaları kullanmamız gerektiğini, aksi takdirde (AK) sürüm ikili dosyalarını kullanmamız gerektiğini belirtiyoruz. Ardından, ilk argümanı paket listesinin bir bölümünü çalıştırmak için kullanıyoruz: Girdi 0.4 için A-F, 0.5 için G-N ve 0.6 için O-Z.

### Running PackageEvaluator

PkgEval'i çalıştırmak için yeterince güçlü bir makine bulun (örneğin Nanosoldier düğümü 1), ardından çalıştırın.

```
git clone https://github.com/JuliaCI/PackageEvaluator.jl.git
cd PackageEvaluator.jl/scripts
git checkout backport-x.y.z
./runvagrant.sh
```

Bu, scripts/ dizininde bazı klasörler üretir. Klasör adları ve içerikleri aşağıda çözülmüştür:

| Folder name | Julia version | Package range |
|:-----------:|:-------------:|:-------------:|
|    0.4AK    |    Release    |      A-F      |
|    0.4LZ    |   Backport    |      A-F      |
|    0.5AK    |    Release    |      G-N      |
|    0.5LZ    |   Backport    |      G-N      |
|    0.6AK    |    Release    |      O-Z      |
|    0.6LZ    |   Backport    |      O-Z      |

### Investigating results

Bunu yaptıktan sonra, aynı dizinden `./summary.sh` komutunu kullanarak bulguların bir özet raporunu oluşturabilirsiniz. Bunu, sürüme göre genel sonuçları toplamak için her bir klasör için yapacağız.

```
./summary.sh 0.4AK/*.json > summary_release.txt
./summary.sh 0.5AK/*.json >> summary_release.txt
./summary.sh 0.6AK/*.json >> summary_release.txt
./summary.sh 0.4LZ/*.json > summary_backport.txt
./summary.sh 0.5LZ/*.json >> summary_backport.txt
./summary.sh 0.6LZ/*.json >> summary_backport.txt
```

Şimdi `summary_release.txt` ve `summary_backport.txt` adında iki dosyamız var, bu dosyalar iki versiyon için her paket için PackageEvaluator test sonuçlarını (geçti/kaldi) içermektedir.

Bu dosyaları Julia'ya daha kolay bir şekilde almak için, bunları CSV dosyalarına dönüştüreceğiz ve ardından sonuçları işlemek için DataFrames paketini kullanacağız. CSV'ye dönüştürmek için, her .txt dosyasını karşılık gelen bir .csv dosyasına kopyalayın, ardından Vim'e girin ve `ggVGI"<esc>` komutunu çalıştırın, ardından `:%s/\.json /",/g` yazın. (Vim kullanmak zorunda değilsiniz; bu sadece bir yol.) Şimdi sonuçları aşağıdaki gibi bir Julia kodu ile işleyin.

```julia
using DataFrames

release = readtable("summary_release.csv", header=false, names=[:package, :release])
backport = readtable("summary_backport.csv", header=false, names=[:package, :backport])

results = join(release, backport, on=:package, kind=:outer)

for result in eachrow(results)
    a = result[:release]
    b = result[:backport]
    if (isna(a) && !isna(b)) || (isna(b) && !isna(a))
        color = :yellow
    elseif a != b && occursin("pass", b)
        color = :green
    elseif a != b
        color = :red
    else
        continue
    end
    printstyled(result[:package], ": Release ", a, " -> Backport ", b, "\n", color=color)
end
```

Bu, `stdout`'a renk kodlu satırlar yazacaktır. Kırmızı olan tüm satırlar, geri portlama sürümünün neden olduğu potansiyel arızaları işaret ettiği için incelenmelidir. Sarı olan satırlar, bir paketin bir sürümde çalıştığını ancak diğerinde bir nedenle çalışmadığını gösterdiği için incelenmelidir. Geri portlanmış dalınızın arızalara neden olduğunu bulursanız, sorunlu commit'leri belirlemek için `git bisect` kullanın, bu commit'leri `git revert` ile geri alın ve süreci tekrarlayın.

## Merging backports into the release branch

Sonra bunu sağladığınızda

  * geri alınmış commitler Julia'nın tüm birim testlerini geçiyor,
  * geri alınan taahhütler ile sürüm dalı arasında performans gerilemeleri yoktur ve
  * geri alınan taahhütler, kayıtlı paketlerden hiçbirini bozmaz,

ardından backport dalı release-x.y'ye birleştirilmek üzere hazırdır. Birleştirildikten sonra, geri taşınan commitleri içeren tüm pull requestlerden "backport pending x.y" etiketini kaldırın. Geri taşınmamış PR'lerden etiketi kaldırmayın.

release-x.y dalı artık tüm yeni commit'leri içermelidir. Dalda yapmak istediğimiz son şey sürüm numarasını ayarlamaktır. Bunu yapmak için, VERSION dosyasını sürüm numarasından `-pre` kısmını kaldıracak şekilde düzenleyen bir PR gönderin. Bu birleştirildikten sonra, etiketlemeye hazırız.

## Tagging the release

Zamanı geldi! release-x.y dalını kontrol edin ve dalınızın yerel kopyasının uzak dal ile güncel olduğundan emin olun. Komut satırında, çalıştırın

```
git tag v$(cat VERSION)
git push --tags
```

Bu, etiketi yerel olarak oluşturur ve GitHub'a gönderir.

Yayımlamayı etiketledikten sonra, y.x sürümüne bir PR daha gönderin, yamanın numarasını artırın ve sonuna `-pre` ekleyin. Bu, dal durumunun x.y serisindeki bir sonraki nokta sürümünün ön sürüm versiyonunu yansıttığını belirtir.

Kalanan talimatları Makefile'da izleyin.

## Signing binaries

Bu adımlardan bazıları güvenli şifreler gerektirecektir. Uygun şifreleri almak için Elliot Saba (staticfloat) veya Alex Arslan (ararslan) ile iletişime geçin. Her platform için kod imzalamanın o platformda gerçekleştirilmesi gerektiğini unutmayın (örneğin, Windows imzalama Windows'ta yapılmalıdır, vb.).

### Linux

Kod imzalama, Linux'ta manuel olarak yapılmalıdır, ancak oldukça basittir. Öncelikle, `juliasecure` AWS kovasındaki CodeSigning klasöründen `julia.key` dosyasını edinin. Bunu GnuPG anahtar halkasına eklemek için

```
gpg --import julia.key
```

Bu, Elliot veya Alex'ten almanız gereken bir şifre girmeyi gerektirecektir. Sonra, anahtarın güven seviyesini maksimuma ayarlayın. Öncelikle bir `gpg` oturumu açarak başlayın:

```
gpg --edit-key julia
```

`trust` yazın, ardından güven düzeyi sorulduğunda mevcut maksimumu (muhtemelen 5) sağlayın. GnuPG'den çıkın.

Şimdi, buildbot'larda oluşturulan her bir Linux tarball'ı için girin

```
gpg -u julia --armor --detach-sig julia-x.y.z-linux-<arch>.tar.gz
```

Bu, her tarball için karşılık gelen bir .asc dosyası üretecektir. Ve hepsi bu kadar!

### macOS

Kod imzalama, macOS buildbot'larında otomatik olarak gerçekleşmelidir. Ancak, bunun başarılı olduğunu doğrulamak önemlidir. macOS çalışan bir sistem veya sanal makinede, buildbot'larda oluşturulan .dmg dosyasını indirin. Örnek olması açısından, .dmg dosyasının adının `julia-x.y.z-osx.dmg` olduğunu varsayalım. Çalıştırın

```
mkdir ./jlmnt
hdiutil mount -readonly -mountpoint ./jlmnt julia-x.y.z-osx.dmg
codesign -v jlmnt/Julia-x.y.app
```

Bağlama işlemi sırasında listelenen montaj diskinin adını not etmeyi unutmayın! Örnek olması açısından bunun `disk3` olduğunu varsayalım. Kod imzalama doğrulaması başarılı bir şekilde tamamlandıysa, `codesign` adımından hiçbir çıktı olmayacaktır. Eğer gerçekten başarılı olduysa, .dmg'yi şimdi ayırabilirsiniz:

```
hdiutil eject /dev/disk3
rm -rf ./jlmnt
```

Eğer şöyle bir mesaj alırsanız

> Julia-x.y.app: kod nesnesi hiç imzalanmamış


o zaman manuel olarak imzalamanız gerekecek.

Manuel imzalamak için önce `juliasecure` kovasındaki CodeSigning klasöründen OS X sertifikalarını alın. .p12 dosyasını Keychain.app kullanarak anahtar zincirinize ekleyin. Anahtarın şifresi için Elliot Saba (staticfloat) veya Alex Arslan (ararslan) ile iletişime geçin. Şimdi çalıştırın

```
hdiutil convert julia-x.y.z-osx.dmg -format UDRW -o julia-x.y.z-osx_writable.dmg
mkdir ./jlmnt
hdiutil mount -mountpoint julia-x.y.z-osx_writable.dmg
codesign -s "AFB379C0B4CBD9DB9A762797FC2AB5460A2B0DBE" --deep jlmnt/Julia-x.y.app
```

Bu, şu mesajla başarısız olabilir gibi

> Julia-x.y.app: kaynak fork'u, Finder bilgisi veya benzeri kalıntılar yasaklandı


Eğer durum böyleyse, gereksiz nitelikleri kaldırmanız gerekecek:

```
xattr -cr jlmnt/Julia-x.y.app
```

Sonra kod imzalamayı tekrar deneyin. Eğer bu hata vermezse, doğrulamayı tekrar deneyin. Eğer her şey şimdi yolundaysa, yazılabilir .dmg'yi çıkartın ve tekrar salt okunur hale getirin:

```
hdiutil eject /dev/disk3
rm -rf ./jlmnt
hdiutil convert julia-x.y.z-osx_writable.dmg -format UDZO -o julia-x.y.z-osx_fixed.dmg
```

Sonuç .dmg dosyasının gerçekten düzeltildiğini doğrulamak için üzerine çift tıklayın. Her şey yolundaysa, çıkartın ve ardından adından `_fixed` ekini kaldırın. Hepsi bu kadar!

### Windows

İmza, Windows'ta manuel olarak gerçekleştirilmelidir. Öncelikle, gerekli imzalama araçlarını içeren Windows 10 SDK'sını Microsoft web sitesinden edinin. `SignTool` aracına ihtiyacımız var, bu da `C:\Program Files (x86)\Windows Kits\10\App Certification Kit` gibi bir yere yüklenmiş olmalıdır. Windows sertifika dosyalarını `juliasecure` üzerindeki CodeSigning'den alın ve bunları yürütülebilir dosyaların bulunduğu aynı dizine koyun. Bir Windows CMD penceresi açın, tüm dosyaların bulunduğu yere `cd` komutunu kullanarak gidin ve çalıştırın.

```
set PATH=%PATH%;C:\Program Files (x86)\Windows Kits\10\App Certification Kit;
signtool sign /f julia-windows-code-sign_2017.p12 /p "PASSWORD" ^
   /t http://timestamp.verisign.com/scripts/timstamp.dll ^
   /v julia-x.y.z-win32.exe
```

Not edin ki `^` Windows CMD'de bir satır devam karakteridir ve `PASSWORD` bu sertifika için şifreyi temsil eden bir yer tutucudur. Her zamanki gibi, şifreler için Elliot veya Alex ile iletişime geçin. Hata yoksa, her şey yolunda!

## Uploading binaries

Artık her şey imzalandığına göre, ikili dosyaları AWS'ye yüklememiz gerekiyor. Cyberduck gibi bir program veya `aws` komut satırı aracını kullanabilirsiniz. İkili dosyalar, uygun klasörlerde `julialang2` kovasına gitmelidir. Örneğin, Linux x86-64 `julialang2/bin/linux/x.y` klasörüne gider. Mevcut `julia-x.y-latest-linux-<arch>.tar.gz` dosyasını silmeyi ve bunun yerine `julia-x.y.z-linux-<arch>.tar.gz` dosyasının bir kopyasını yüklemeyi unutmayın.

Her şeyin, kaynak tarballarının ve tüm sürüm ikili dosyalarının kontrol toplamlarını yüklememiz de gerekiyor. Bu basit:

```
shasum -a 256 julia-x.y.z* | grep -v -e sha256 -e md5 -e asc > julia-x.y.z.sha256
md5sum julia-x.y.z* | grep -v -e sha256 -e md5 -e asc > julia-x.y.z.md5
```

Not edin ki, bu komutları macOS'ta çalıştırıyorsanız, çıktınızda çok az farklılıklar göreceksiniz; bu farklılıkları mevcut bir dosyaya bakarak yeniden biçimlendirebilirsiniz. Mac kullanıcıları ayrıca `md5sum` yerine `md5 -r` kullanmak zorundadır. .md5 ve .sha256 dosyalarını AWS'deki `julialang2/bin/checksums` dizinine yükleyin.

AWS'ye yüklenen tüm dosyaların izinlerinin "Herkes: OKUMA" olarak ayarlandığından emin olun.

Her yüklediğimiz dosya için, web sitesindeki bağlantıların güncellenmiş dosyalara işaret etmesi için Fastly önbelleğini temizlememiz gerekiyor. Bir örnek olarak:

```
curl -X PURGE https://julialang-s3.julialang.org/bin/checksums/julia-x.y.z.sha256
```

Bazen bu gerekli değildir ama yine de yapmak iyidir.
