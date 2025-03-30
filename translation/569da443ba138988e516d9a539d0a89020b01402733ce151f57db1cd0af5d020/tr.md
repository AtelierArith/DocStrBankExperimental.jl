# Building Julia (Detailed)

## Downloading the Julia source code

Eğer bir güvenlik duvarının arkasındaysanız, `git` protokolü yerine `https` protokolünü kullanmanız gerekebilir:

```sh
git config --global url."https://".insteadOf git://
```

Sisteminizin uygun proxy ayarlarını kullanacak şekilde yapılandırıldığından emin olun, örneğin `https_proxy` ve `http_proxy` değişkenlerini ayarlayarak.

## Building Julia

İlk kez derlendiğinde, derleme otomatik olarak önceden derlenmiş [external dependencies](#Required-Build-Tools-and-External-Libraries) dosyasını indirecektir. Tüm bağımlılıkları kendiniz derlemeyi tercih ediyorsanız veya derleme süreci sırasında ağa erişemeyen bir sistemde derleme yapıyorsanız, `Make.user` dosyasına aşağıdakileri ekleyin:

```
USE_BINARYBUILDER=0
```

Julia'yı inşa etmek, tüm bağımlılıkları inşa etmek için 5GiB ve yaklaşık 4GiB sanal bellek gerektirir.

Paralel bir derleme yapmak için `make -j N` komutunu kullanın ve maksimum eşzamanlı işlem sayısını belirtin. Derlemedeki varsayılan ayarlar sizin için işe yaramıyorsa ve belirli make parametrelerini ayarlamanız gerekiyorsa, bunları `Make.user` dosyasına kaydedebilir ve dosyayı Julia kaynaklarınızın köküne yerleştirebilirsiniz. Derleme, `Make.user` dosyasının varlığını otomatik olarak kontrol edecek ve eğer mevcutsa kullanacaktır.

Julia'nın ağaç dışı derlemelerini oluşturmak için komut satırında `make O=<build-directory> configure` belirtebilirsiniz. Bu, belirtilen dizinde Julia'yı derlemek için gerekli tüm Makefile'ların bulunduğu bir dizin kopyası oluşturacaktır. Bu derlemeler, Julia'daki kaynak dosyalarını ve `deps/srccache`'i paylaşacaktır. Her ağaç dışı derleme dizininin, üst düzey klasördeki global `Make.user` dosyasını geçersiz kılmak için kendi `Make.user` dosyası olabilir.

Her şey doğru çalışıyorsa, bir Julia afişi ve değerlendirme için ifadeler girebileceğiniz etkileşimli bir istem göreceksiniz. (Kütüphanelerle ilgili hatalar, PATH'inizde eski, uyumsuz kütüphanelerin bulunmasından kaynaklanabilir. Bu durumda, `julia` dizinini PATH'te daha öne taşımayı deneyin). Yukarıdaki talimatların çoğunun unix sistemlerine uygulandığını unutmayın.

Her yerde julia çalıştırmak için şunları yapabilirsiniz:

  * bir takma ad ekleyin (bash'te: `echo "alias julia='/path/to/install/folder/bin/julia'" >> ~/.bashrc && source ~/.bashrc`), veya
  * `julia` yürütülebilir dosyasına `julia` dizininde bir yumuşak bağlantı ekleyin ve bunu `/usr/local/bin` (veya yolunuzda zaten bulunan uygun bir dizin) içine yerleştirin, veya
  * bu shell oturumunuz için `julia` dizinini çalıştırılabilir yolunuza ekleyin ( `bash` için: `export PATH="$(pwd):$PATH"` ; `csh` veya `tcsh` için:

`set path= ( $path $cwd )` ), veya

  * `julia` dizinini yürütülebilir yolunuza kalıcı olarak ekleyin (örneğin, `.bash_profile` içinde), veya
  * `Make.user` dosyasına `prefix=/path/to/install/folder` yazın ve ardından `make install` komutunu çalıştırın. Eğer bu klasörde zaten yüklü bir Julia sürümü varsa, `make install` komutunu çalıştırmadan önce onu silmelisiniz.

Julia'nın derlemesini kontrol etmek için ayarlayabileceğiniz bazı seçenekler, `Make.inc` dosyasının başında listelenmiş ve belgelenmiştir, ancak bu amaçla asla düzenlememelisiniz, bunun yerine `Make.user` dosyasını kullanın.

Julia'nın Makefile'ları, değişkenlerin değerlerini yazdırmak için `print-<VARNAME>` adlı kullanışlı otomatik kurallar tanımlar; burada `<VARNAME>`, yazdırılacak değişkenin adını temsil eder. Örneğin

```console
$ make print-JULIA_PRECOMPILE
JULIA_PRECOMPILE=1
```

Bu kurallar hata ayıklama amaçları için faydalıdır.

Artık Julia'yı şöyle çalıştırabilmelisiniz:

```
julia
```

Eğer Linux, macOS veya Windows üzerinde dağıtım için bir Julia paketi oluşturuyorsanız, [distributing.md](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/distributing.md) adresindeki detaylı notlara göz atın.

## Updating an existing source tree

Eğer daha önce `git clone` kullanarak `julia` indirdiyseniz, yeni bir başlangıç yapmak yerine mevcut kaynak ağacını `git pull` ile güncelleyebilirsiniz:

```sh
cd julia
git pull && make
```

Varsayıldığı gibi, kaynak ağacında yukarı akış güncellemeleriyle çelişen herhangi bir değişiklik yapmadıysanız, bu komutlar en son sürüme güncellemek için bir derleme tetikleyecektir.

## General troubleshooting

1. Zamanla, temel kütüphane yeterince değişiklik biriktirebilir, böylece sistem görüntüsünü oluşturma sürecinde başlatma işlemi başarısız olur. Eğer bu olursa, derleme bir hata ile başarısız olabilir, örneğin

    ```sh
     *** This error is usually fixed by running 'make clean'. If the error persists, try 'make cleanall' ***
    ```

    Açıklandığı gibi, `make clean && make` çalıştırmak genellikle yeterlidir. Bazen, `make cleanall` ile yapılan daha güçlü bir temizleme gereklidir.
2. Yeni sürümleri dış bağımlılıkların tanıtılabilir, bu da zaman zaman eski sürümlerin mevcut derlemeleriyle çelişkilere neden olabilir.

    a. Özel `make` hedefleri, bir bağımlılığın mevcut derlemesini silmeye yardımcı olmak için vardır. Örneğin, `make -C deps clean-llvm` mevcut `llvm` derlemesini temizleyecek, böylece `llvm` bir sonraki `make` çağrısında indirilen kaynak dağıtımından yeniden derlenecektir. `make -C deps distclean-llvm` daha güçlü bir silme işlemi olup, indirilen kaynak dağıtımını da silecektir; bu, bir sonraki `make` çağrısında kaynak dağıtımının taze bir kopyasının indirileceğini ve herhangi bir yeni yamanın uygulanacağını garanti eder.

    b. Mevcut `julia` ikili dosyalarını ve tüm bağımlılıklarını silmek için, kaynak ağacındaki `./usr` dizinini silin.
3. Eğer macOS'u yakın zamanda güncellediyseniz, komut satırı araçlarını güncellemek için `xcode-select --install` komutunu çalıştırdığınızdan emin olun. Aksi takdirde, `ld: library not found for -lcrt1.10.6.o` gibi eksik başlıklar ve kütüphaneler için hatalarla karşılaşabilirsiniz.
4. Eğer kaynak dizini taşıdıysanız, `CMake Error: The current CMakeCache.txt directory ... is different than the directory ... where CMakeCache.txt was created.` gibi hatalar alabilirsiniz. Bu durumda, `deps` altında sorunlu bağımlılığı silebilirsiniz.
5. Aşırı durumlarda, kaynak ağacını temiz bir duruma sıfırlamak isteyebilirsiniz. Aşağıdaki git komutları faydalı olabilir:

    ```sh
     git reset --hard #Forcibly remove any changes to any files under version control
     git clean -x -f -d #Forcibly remove any file or directory not under version control
    ```

    *Çalışmanızı kaybetmemek için, bu komutların ne yaptığını bildiğinizden emin olun. `git` bu değişiklikleri geri alamayacaktır!*

## Platform-Specific Notes

Farklı işletim sistemleri için notlar:

  * [Linux](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/linux.md)
  * [macOS](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/macos.md)
  * [Windows](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/windows.md)
  * [FreeBSD](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/freebsd.md)

Farklı mimariler için notlar:

  * [ARM](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/arm.md)

## Required Build Tools and External Libraries

Julia'yı inşa etmek için aşağıdaki yazılımların kurulu olması gerekmektedir:

  * **[GNU make]**                — bağımlılıkları oluşturma.
  * **[gcc & g++][gcc]** (>= 7.1) veya **[Clang][clang]** (>= 5.0, >= 9.3 Apple Clang için) — C, C++ derleme ve bağlama.
  * **[libatomic][gcc]**          — **[gcc]** tarafından sağlanır ve atomik işlemleri desteklemek için gereklidir.
  * **[python]** (>=2.7)          — LLVM'yi inşa etmek için gereklidir.
  * **[gfortran]**                — Fortran kütüphanelerini derleme ve bağlama.
  * **[perl]**                    — kütüphanelerin başlık dosyalarının ön işlenmesi.
  * **[wget]**, **[curl]**, veya **[fetch]** (FreeBSD) — harici kütüphaneleri otomatik olarak indirmek için.
  * **[m4]**                      — GMP'yi inşa etmek için gerekli.
  * **[awk]**                     — Makefile'lar için yardımcı araç.
  * **[yaman]**                   — kaynak kodunu değiştirmek için.
  * **[cmake]** (>= 3.4.3)        — `libgit2` inşa etmek için gereklidir.
  * **[pkg-config]**              — `libgit2`'yi doğru bir şekilde inşa etmek için gereklidir, özellikle proxy desteği için.
  * **[powershell]** (>= 3.0)     — yalnızca Windows'ta gereklidir.
  * **[hangi]**                   — yapı bağımlılıklarını kontrol etmek için gereklidir.

Debian tabanlı dağıtımlarda (örneğin Ubuntu), bunları `apt-get` ile kolayca kurabilirsiniz:

```
sudo apt-get install build-essential libatomic1 python gfortran perl wget m4 cmake pkg-config curl
```

Julia aşağıdaki dış kütüphaneleri kullanır; bu kütüphaneler otomatik olarak indirilir (veya birkaç durumda, Julia kaynak deposunda dahil edilir) ve ardından `make` komutunu ilk kez çalıştırdığınızda kaynak kodundan derlenir. Julia'nın kullandığı bu kütüphanelerin belirli sürüm numaraları [`deps/$(libname).version`](https://github.com/JuliaLang/julia/blob/master/deps/) olarak listelenmiştir:

  * **[LLVM]** (15.0 + [patches](https://github.com/JuliaLang/llvm-project/tree/julia-release/15.x)) — derleyici altyapısı (bkz. [note below](#llvm)).
  * **[FemtoLisp]**            — Julia kaynak kodu ile paketlenmiş ve derleyici ön yüzünü uygulamak için kullanılmıştır.
  * **[libuv]**  (özel çatal) — taşınabilir, yüksek performanslı olay tabanlı G/Ç kütüphanesi.
  * **[OpenLibm]**             — taşınabilir libm kütüphanesi, temel matematik fonksiyonlarını içerir.
  * **[DSFMT]**                — hızlı Mersenne Twister sahte rastgele sayı üreteci kütüphanesi.
  * **[OpenBLAS]**             — hızlı, açık ve sürdürülen [temel lineer cebir alt programları (BLAS)]
  * **[LAPACK]**               — eşzamanlı lineer denklemler sistemlerini çözmek, lineer denklemler sistemlerinin en küçük kareler çözümleri, özdeğer problemleri ve tekil değer problemleri için lineer cebir rutinleri kütüphanesi.
  * **[MKL]** (isteğe bağlı)       – OpenBLAS ve LAPACK, Intel'in MKL kütüphanesi ile değiştirilebilir.
  * **[SuiteSparse]**          — seyrek matrisler için lineer cebir rutinleri kütüphanesi.
  * **[PCRE]**                 — Perl uyumlu düzenli ifadeler kütüphanesi.
  * **[GMP]**                  — GNU çoklu hassasiyet aritmetiği kütüphanesi, `BigInt` desteği için gereklidir.
  * **[MPFR]**                 — GNU çoklu hassasiyetli kayan nokta kütüphanesi, keyfi hassasiyetli kayan nokta (`BigFloat`) desteği için gereklidir.
  * **[libgit2]**              — Julia paket yöneticisi tarafından kullanılan, Git ile bağlantılı kütüphane.
  * **[curl]**                 — libcurl indirme ve proxy desteği sağlar.
  * **[libssh2]**              — SSH taşınması için bir kütüphane, SSH uzakları olan paketler için libgit2 tarafından kullanılır.
  * **[mbedtls]**              — kriptografi ve taşıma katmanı güvenliği için kullanılan kütüphane, libssh2 tarafından kullanılır.
  * **[utf8proc]**             — UTF-8 kodlu Unicode dizelerini işlemek için bir kütüphane.
  * **[LLVM libunwind]**       — LLVM'nin [libunwind] kütüphanesinin bir çatalı, bir programın çağrı zincirini belirleyen bir kütüphanedir.
  * **[ITTAPI]**               — Intel'in Enstrümantasyon ve İzleme Teknolojisi ve Anında API.

[GNU make]:     https://www.gnu.org/software/make [patch]:        https://www.gnu.org/software/patch [wget]:         https://www.gnu.org/software/wget [m4]:           https://www.gnu.org/software/m4 [awk]:          https://www.gnu.org/software/gawk [gcc]:          https://gcc.gnu.org [clang]:        https://clang.llvm.org [python]:       https://www.python.org/ [gfortran]:     https://gcc.gnu.org/fortran/ [curl]:         https://curl.haxx.se [fetch]:        https://www.freebsd.org/cgi/man.cgi?fetch(1) [perl]:         https://www.perl.org [cmake]:        https://www.cmake.org [OpenLibm]:     https://github.com/JuliaLang/openlibm [DSFMT]:        https://github.com/MersenneTwister-Lab/dSFMT [OpenBLAS]:     https://github.com/xianyi/OpenBLAS [LAPACK]:       https://www.netlib.org/lapack [MKL]:          https://software.intel.com/en-us/articles/intel-mkl [SuiteSparse]:  https://people.engr.tamu.edu/davis/suitesparse.html [PCRE]:         https://www.pcre.org [LLVM]:         https://www.llvm.org [LLVM libunwind]: https://github.com/llvm/llvm-project/tree/main/libunwind [FemtoLisp]:    https://github.com/JeffBezanson/femtolisp [GMP]:          https://gmplib.org [MPFR]:         https://www.mpfr.org [libuv]:        https://github.com/JuliaLang/libuv [libgit2]:      https://libgit2.org/ [utf8proc]:     https://julialang.org/utf8proc/ [libunwind]:    https://www.nongnu.org/libunwind [libssh2]:      https://www.libssh2.org [mbedtls]:      https://tls.mbed.org/ [pkg-config]:   https://www.freedesktop.org/wiki/Software/pkg-config/ [powershell]:   https://docs.microsoft.com/en-us/powershell/scripting/wmf/overview [which]:        https://carlowood.github.io/which/ [ITTAPI]:       https://github.com/intel/ittapi

## Build dependencies

Eğer sisteminizde bu paketlerden bir veya daha fazlası zaten yüklüyse, `USE_SYSTEM_...=1` ifadesini `make` komutuna geçirerek veya `Make.user` dosyasına bu satırı ekleyerek Julia'nın bu kütüphanelerin kopyalarını derlemesini engelleyebilirsiniz. Olası bayrakların tam listesi `Make.inc` dosyasında bulunabilir.

Lütfen bu prosedürün resmi olarak desteklenmediğini unutmayın, çünkü bağımlılıkların kurulumu ve sürümlemesine ek değişkenlikler getirir ve yalnızca sistem paket yöneticileri için önerilmektedir. Beklenmedik derleme hataları oluşabilir, çünkü derleme sistemi, uygun paketlerin yüklü olduğunu sağlamak için daha fazla kontrol yapmayacaktır.

### LLVM

En karmaşık bağımlılık LLVM'dir, bunun için yukarıdan ek yamalar gerekmektedir (LLVM geriye dönük uyumlu değildir).

Julia'yı LLVM ile paketlemek için, ya şunları öneriyoruz:

  * Julia paketinin içine yalnızca Julia'ya ait bir LLVM kütüphanesini paketlemek veya
  * LLVM paketine yamaları eklemek.

      * Tamam bir yamanın tam listesi [Github](https://github.com/JuliaLang/llvm-project) adresinde mevcuttur, `julia-release/15.x` dalına bakın.
      * Tek tek Julia'ya özgü yamanın lib yeniden adlandırması (`llvm7-symver-jlprefix.patch`) olduğunu, bunun sistem LLVM'ye *uygulanmaması* gerektiğini belirtir.
      * Kalan kalan yamalar tamamen yukarı akış hata düzeltmeleridir ve yukarı akış LLVM'ye katkıda bulunulmuştur.

Yamanlanmamış veya farklı bir LLVM sürümü kullanmak hatalara ve/veya kötü performansa yol açacaktır. `Make.user` dosyasında aşağıdaki seçeneklerle bir uzak Git deposundan farklı bir LLVM sürümü oluşturabilirsiniz:

```make
# Force source build of LLVM
USE_BINARYBUILDER_LLVM = 0
# Use Git for fetching LLVM source code
# this is either `1` to get all of them
DEPS_GIT = 1
# or a space-separated list of specific dependencies to download with git
DEPS_GIT = llvm

# Other useful options:
#URL of the Git repository you want to obtain LLVM from:
#  LLVM_GIT_URL = ...
#Name of the alternate branch to clone from git
#  LLVM_BRANCH = julia-16.0.6-0
#SHA hash of the alterate commit to check out automatically
#  LLVM_SHA1 = $(LLVM_BRANCH)
#List of LLVM targets to build.  It is strongly recommended to keep at least all the
#default targets listed in `deps/llvm.mk`, even if you don't necessarily need all of them.
#  LLVM_TARGETS = ...
#Use ccache for faster recompilation in case you need to restart a build.
#  USECCACHE = 1
#  CMAKE_GENERATOR=Ninja
#  LLVM_ASSERTIONS=1
#  LLVM_DEBUG=Symbols
```

Çeşitli derleme aşamaları belirli dosyalar tarafından kontrol edilir:

  * `deps/llvm.version` : yeni bir sürümü kontrol etmek için dokunun veya değiştirin, `make get-llvm check-llvm`
  * `deps/srccache/llvm/source-extracted` : `make extract-llvm` sonucudur.
  * `deps/llvm/build_Release*/build-configured` : `make configure-llvm` sonucudur.
  * `deps/llvm/build_Release*/build-configured` : `make compile-llvm` sonucudur.
  * `usr-staging/llvm/build_Release*.tgz` : `make stage-llvm` sonucudur (yeniden oluşturmak için `make reinstall-llvm` kullanın)
  * `usr/manifest/llvm` : `make install-llvm` sonucudur (yeniden oluşturmak için `make uninstall-llvm` kullanın)
  * `make version-check-llvm` : her zaman çalışır ve kullanıcıyı yerel değişiklikler varsa uyarır.

Julia'nın daha yeni LLVM sürümleriyle oluşturulabilmesine rağmen, bunun desteği deneysel olarak değerlendirilmelidir ve paketleme için uygun değildir.

### libuv

Julia, özel bir libuv çatalı kullanıyor. Bu küçük bir bağımlılıktır ve Julia ile aynı pakette güvenle birleştirilebilir, sistem kütüphanesiyle çakışmaz. Julia derlemeleri, sistem libuv'yi kullanmaya *çalışmamalıdır*.

### BLAS and LAPACK

Yüksek performanslı bir sayısal dil olan Julia, OpenBLAS veya ATLAS gibi çok iş parçacıklı BLAS ve LAPACK ile bağlantılı olmalıdır; bu, bazı sistemlerde varsayılan olabilecek referans `libblas` uygulamalarından çok daha iyi performans sağlayacaktır.

## Source distributions of releases

Her pre-release ve sürüm Julia'nın bir "tam" kaynak dağıtımı ve bir "hafif" kaynak dağıtımı vardır.

Tam bir kaynak dağıtımı, Julia'nın kaynak kodunu ve tüm bağımlılıkları içerir, böylece internet bağlantısı olmadan kaynak kodundan derlenebilir. Hafif kaynak dağıtımı, bağımlılıkların kaynak kodunu içermez.

Örneğin, `julia-1.0.0.tar.gz`, Julia'nın `v1.0.0` sürümü için hafif kaynak dağıtımıdır, `julia-1.0.0-full.tar.gz` ise tam kaynak dağıtımıdır.

## Building Julia from source with a Git checkout of a stdlib

Eğer bir stdlib'in Git checkout'u ile Julia'yı kaynak kodundan derlemeniz gerekiyorsa, Julia'yı derlerken `make DEPS_GIT=NAME_OF_STDLIB` komutunu kullanın.

Örneğin, Pkg'nin Git checkout'u ile Julia'yı kaynak kodundan derlemeniz gerekiyorsa, Julia'yı derlerken `make DEPS_GIT=Pkg` komutunu kullanın. `Pkg` deposu `stdlib/Pkg` içinde yer alır ve başlangıçta ayrılmış bir `HEAD` ile oluşturulmuştur. Eğer bunu önceden var olan bir Julia deposundan yapıyorsanız, öncelikle `make clean` komutunu kullanmanız gerekebilir.

Eğer birden fazla stdlib'in Git checkout'ları ile Julia'yı kaynak kodundan derlemeniz gerekiyorsa, `DEPS_GIT` stdlib adlarının boşlukla ayrılmış bir listesi olmalıdır. Örneğin, Pkg, Tar ve Downloads'un Git checkout'u ile Julia'yı kaynak kodundan derlemeniz gerekiyorsa, Julia'yı derlerken `make DEPS_GIT='Pkg Tar Downloads'` komutunu kullanın.

## Building an "assert build" of Julia

Bir "assert build" (doğrulama derlemesi) Julia'nın hem `FORCE_ASSERTIONS=1` hem de `LLVM_ASSERTIONS=1` ile derlendiği bir derlemedir. Bir doğrulama derlemesi oluşturmak için, `Make.user` dosyanızda aşağıdaki iki değişkeni de tanımlayın:

```
FORCE_ASSERTIONS=1
LLVM_ASSERTIONS=1
```

Lütfen dikkat edin ki, Julia'nın assert derlemeleri, normal (assert olmayan) derlemelerden daha yavaş olacaktır.

## Building 32-bit Julia on a 64-bit machine

Bazen 32-bit mimarilere özgü hatalar ortaya çıkabilir ve bu olduğunda, sorunu yerel makinenizde hata ayıklamak faydalı olabilir. Çoğu modern 64-bit sistem, 32-bit için derlenmiş programları çalıştırmayı desteklediğinden, Julia'yı kaynak kodundan yeniden derlemeniz gerekmiyorsa (örneğin, 32-bit Julia'nın davranışını C koduna dokunmadan incelemeniz gerekiyorsa), sisteminiz için [official downloads page](https://julialang.org/downloads/) adresinden edinebileceğiniz bir 32-bit Julia derlemesini kullanabilirsiniz. Ancak, Julia'yı kaynak kodundan yeniden derlemeniz gerekiyorsa, bir seçenek 32-bit bir sistemin Docker konteynerini kullanmaktır. En azından şu an için, [ubuntu 32-bit docker images](https://hub.docker.com/r/i386/ubuntu) kullanarak 32-bit bir Julia sürümü oluşturmak oldukça basittir. Kısacası, `docker`'ı kurduktan sonra gerekli adımlar şunlardır:

```sh
$ docker pull i386/ubuntu
$ docker run --platform i386 -i -t i386/ubuntu /bin/bash
```

Bu noktada 32-bit bir makine konsolunda olmalısınız (not edin ki `uname` ana mimariyi rapor eder, bu nedenle hala 64-bit olarak görünebilir, ancak bu Julia derlemesini etkilemeyecektir). Paketler ekleyebilir ve kod derleyebilirsiniz; `exit` komutunu verdiğinizde, tüm değişiklikler kaybolacaktır, bu yüzden analizlerinizi tek bir oturumda tamamladığınızdan emin olun veya ortamınızı kurmak için kullanabileceğiniz kopyala/yapıştır bir betik oluşturun.

Bu noktadan itibaren, yapmalısınız

```sh
# apt update
```

(Not edin `sudo` kurulu değil, ama gerekli de değil çünkü `root` olarak çalışıyorsunuz, bu yüzden tüm komutlardan `sudo`'yu çıkarabilirsiniz.)

Sonra tüm [build dependencies](#required-build-tools-and-external-libraries), tercih ettiğiniz bir konsol tabanlı editör, `git` ve ihtiyacınız olan diğer her şeyi (örn. `gdb`, `rr` vb.) ekleyin. Çalışmak için bir dizin seçin ve `git clone` ile Julia'yı klonlayın, hata ayıklamak istediğiniz dalı kontrol edin ve Julia'yı her zamanki gibi derleyin.

## Update the version number of a dependency

İki tür yapı vardır

1. Her şeyi (`deps/` ve `src/`) kaynak kodundan inşa edin.  (`Make.user` dosyasına `USE_BINARYBUILDER=0` ekleyin, bkz. [Building Julia](#building-julia))
2. Kaynaklardan inşa et (`src/`) önceden derlenmiş bağımlılıklarla (varsayılan)

`deps/` içindeki bir bağımlılığın sürüm numarasını güncellemek istediğinizde, aşağıdaki kontrol listesini kullanmak isteyebilirsiniz:

```md
### Check list

Version numbers:
- [ ] `deps/$(libname).version`: `LIBNAME_VER`, `LIBNAME_BRANCH`, `LIBNAME_SHA1` and `LIBNAME_JLL_VER`
- [ ] `stdlib/$(LIBNAME_JLL_NAME)_jll/Project.toml`: `version`

Checksum:
- [ ] `deps/checksums/$(libname)`
- [ ] `deps/checksums/$(LIBNAME_JLL_NAME)-*/`: `md5` and `sha512`

Patches:
- [ ] `deps/$(libname).mk`
- [ ] `deps/patches/$(libname)-*.patch`
```

Not:

  * Belirli bağımlılıklar için, kontrol listesindeki bazı maddeler mevcut olmayabilir.
  * Checksum dosyası için, **bir uzantısı olmayan tek bir dosya** veya **iki dosya içeren bir klasör** olabilir.

### Example: `OpenLibm`

1. `deps/openlibm.version` dosyasındaki sürüm numaralarını güncelleyin.

      * `OPENLIBM_VER := 0.X.Y`
      * `OPENLIBM_BRANCH = v0.X.Y`
      * `OPENLIBM_SHA1 = yeni-sha1-hash`
2. `stdlib/OpenLibm_jll/Project.toml` dosyasındaki sürüm numarasını güncelleyin.

      * `version = "0.X.Y+0"`
3. `deps/checksums/openlibm` içindeki kontrol toplamlarını güncelleyin.

      * `make -f contrib/refresh_checksums.mk openlibm`
4. `deps/patches/openlibm-*.patch` dosyalarının varlığını kontrol et

      * eğer yamalar yoksa, atla.
      * eğer yamalar varsa, bunların yeni sürüme eklenip eklenmediğini kontrol edin ve kaldırılması gerekip gerekmediğini belirleyin. Bir yama silerken, ilgili Makefile dosyasını (`deps/openlibm.mk`) değiştirmeyi unutmayın.
