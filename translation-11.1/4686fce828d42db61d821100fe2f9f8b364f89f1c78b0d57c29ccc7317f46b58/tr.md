# Windows

Bu dosya, Windows'ta Julia'nın nasıl kurulacağını, oluşturulacağını ve kullanılacağını açıklar.

Daha genel bilgi için Julia hakkında lütfen [main README](https://github.com/JuliaLang/julia/blob/master/README.md) veya [documentation](https://docs.julialang.org) adresine bakın.

## General Information for Windows

Julia'yı modern bir terminal uygulaması kullanarak çalıştırmanızı şiddetle tavsiye ederiz, özellikle Windows Terminal'ı, bu [Microsoft Store](https://aka.ms/terminal) adresinden yükleyebilirsiniz.

### Line endings

Julia yalnızca ikili mod dosyalarını kullanır. Diğer birçok Windows programının aksine, bir dosyaya `\n` yazarsanız, dosyada `\n` alırsınız, başka bir bit deseni değil. Bu, diğer işletim sistemlerinin sergilediği davranışla eşleşir. Windows için Git'i yüklediyseniz, sistem Git'inizi aynı kuralı kullanacak şekilde yapılandırmanız önerilir, ancak zorunlu değildir:

```sh
git config --global core.eol lf
git config --global core.autocrlf input
```

veya `%USERPROFILE%\.gitconfig` dosyasını düzenleyin ve şu satırları ekleyin/düzenleyin:

```
[core]
    eol = lf
    autocrlf = input
```

## Binary distribution

Windows için ikili dağıtım kurulum notları için lütfen [https://julialang.org/downloads/platform/#windows](https://julialang.org/downloads/platform/#windows) adresindeki talimatlara bakın.

## Source distribution

### Cygwin-to-MinGW cross-compiling

Windows'ta Julia'yı kaynak kodundan derlemenin önerilen yolu, Cygwin'in paket yöneticisi aracılığıyla mevcut olan MinGW-w64 derleyici sürümlerini kullanarak [Cygwin](https://www.cygwin.com) adresinden çapraz derleme yapmaktır.

1. Cygwin kurulumunu [32 bit](https://cygwin.com/setup-x86.exe) veya [64 bit](https://cygwin.com/setup-x86_64.exe) için indirin ve çalıştırın. Not: Hem 32 bit hem de 64 bit Cygwin'den 32 veya 64 bit Julia derleyebilirsiniz. 64 bit Cygwin, biraz daha küçük ama genellikle daha güncel bir paket seçeneğine sahiptir.

    *Gelişmiş*: adım 2-4'ü atlayarak çalıştırabilirsiniz:

    ```sh
    setup-x86_64.exe -s <url> -q -P cmake,gcc-g++,git,make,patch,curl,m4,python3,p7zip,mingw64-i686-gcc-g++,mingw64-i686-gcc-fortran,mingw64-x86_64-gcc-g++,mingw64-x86_64-gcc-fortran
    ```

    replacing `<url>` with a site from [https://cygwin.com/mirrors.html](https://cygwin.com/mirrors.html) or run setup manually first and select a mirror.
2. Kurulum konumunu ve indirmek için bir ayna seçin.
3. *Paketleri Seç* adımında, aşağıdakileri seçin:

    1. *Devel* kategorisinden: `cmake`, `gcc-g++`, `git`, `make`, `patch`
    2. *Net* kategorisinden: `curl`
    3. *Yorumlayıcılar* (veya *Python*) kategorisinden: `m4`, `python3`
    4. *Arşiv* kategorisinden: `p7zip`
    5. 32 bit Julia için ve ayrıca *Devel* kategorisinden:  `mingw64-i686-gcc-g++` ve `mingw64-i686-gcc-fortran`
    6. 64 bit Julia için ve ayrıca *Devel* kategorisinden:  `mingw64-x86_64-gcc-g++` ve `mingw64-x86_64-gcc-fortran`
4. Cygwin kurulumunun tamamlanmasına izin verin, ardından kurulu kısayoldan *'Cygwin Terminal'* veya *'Cygwin64 Terminal'* ile başlayın.
5. Julia ve bağımlılıklarını kaynaktan derleyin:

    1. Julia kaynaklarını alın

        ```sh
        git clone https://github.com/JuliaLang/julia.git
        cd julia
        ```

        İpucu: Eğer git'ten `error: cannot fork() for fetch-pack: Resource temporarily unavailable` hatası alıyorsanız, `~/.bashrc` dosyanıza `alias git="env PATH=/usr/bin git"` ekleyin ve Cygwin'i yeniden başlatın.
    2. `Make.user` dosyasındaki `XC_HOST` değişkenini MinGW-w64 çapraz derleme gösterecek şekilde ayarlayın.

        ```sh
        echo 'XC_HOST = i686-w64-mingw32' > Make.user     # for 32 bit Julia
        # or
        echo 'XC_HOST = x86_64-w64-mingw32' > Make.user   # for 64 bit Julia
        ```
    3. Başlat inşaat

        ```sh
        make -j 4       # Adjust the number of threads (4) to match your build environment.
        make -j 4 debug # This builds julia-debug.exe
        ```
6. Julia'yı doğrudan Julia yürütücüleri kullanarak çalıştırın

    ```sh
    usr/bin/julia.exe
    usr/bin/julia-debug.exe
    ```

!!! note "Pro tip: build both!"
    ```sh
    make O=julia-win32 configure
    make O=julia-win64 configure
    echo 'XC_HOST = i686-w64-mingw32' > julia-win32/Make.user
    echo 'XC_HOST = x86_64-w64-mingw32' > julia-win64/Make.user
    echo 'ifeq ($(BUILDROOT),$(JULIAHOME))
            $(error "in-tree build disabled")
          endif' >> Make.user
    make -C julia-win32  # build for Windows x86 in julia-win32 folder
    make -C julia-win64  # build for Windows x86-64 in julia-win64 folder
    ```


### Compiling with MinGW/MSYS2

[MSYS2](https://www.msys2.org/) Windows için bir yazılım dağıtım ve derleme ortamıdır.

Not: MSYS2, **64 bit** Windows 7 veya daha yenisini gerektirir.

1. MSYS2'yi yükleyin ve yapılandırın.

    1. En son [64-bit](https://github.com/msys2/msys2-installer/releases/latest) dağıtımının en son yükleyicisini indirin ve çalıştırın. Yükleyicinin adı `msys2-x86_64-yyyymmdd.exe` gibi olacaktır.
    2. MSYS2 kabuğunu açın. Paket veritabanını ve temel paketleri güncelleyin:

        `pacman -Syu`
    3. MSYS2'yi kapatın ve yeniden başlatın. Temel paketlerin geri kalanını güncelleyin:

        `pacman -Syu`
    4. Sonra julia'yı inşa etmek için gerekli araçları kurun:

        `pacman -S cmake diffutils git m4 make patch tar p7zip curl python`

        64 bit Julia için x86_64 sürümünü yükleyin:

        `pacman -S mingw-w64-x86_64-gcc`

        32 bit Julia için i686 sürümünü yükleyin:

        `pacman -S mingw-w64-i686-gcc`
    5. MSYS2 yapılandırması tamamlandı. Şimdi MSYS2 kabuğundan `çık` yapın.
2. Julia ve önceden derlenmiş bağımlılıkları ile birlikte derleyin.

    1. Yeni bir [**MINGW64/MINGW32 shell**](https://www.msys2.org/docs/environments/#overview) açın. Şu anda hem mingw32 hem de mingw64'ü kullanamıyoruz, bu nedenle x86_64 ve i686 sürümlerini oluşturmak istiyorsanız, her bir ortamda ayrı ayrı inşa etmeniz gerekecek.
    2. Julia kaynaklarını klonlayın:

        `git klon https://github.com/JuliaLang/julia.git  cd julia`
    3. Başlat inşaat

        `make -j$(nproc)`

!!! note "Pro tip: build in dir"
    ```sh
    make O=julia-mingw-w64 configure
    echo 'ifeq ($(BUILDROOT),$(JULIAHOME))
            $(error "in-tree build disabled")
          endif' >> Make.user
    make -C julia-mingw-w64
    ```


### Cross-compiling from Unix (Linux/Mac/WSL)

MinGW-w64 çap derleyicilerini kullanarak Linux, Mac veya Windows Alt Sistemi için Linux (WSL) üzerinden Julia'nın bir Windows sürümünü oluşturabilirsiniz.

Öncelikle, sisteminizin gerekli bağımlılıkları karşıladığından emin olmalısınız. Wine (>=1.7.5), bir sistem derleyicisi ve bazı indirme araçlarına ihtiyacımız var. Not: WSL kullanıyorsanız, bir Cygwin kurulumu bu yöntemi etkileyebilir.

**Ubuntu'da** (diğer Linux sistemlerinde bağımlılık adları muhtemelen benzer olacaktır):

```sh
apt-get install wine-stable gcc wget p7zip-full winbind mingw-w64 gfortran-mingw-w64
dpkg --add-architecture i386 && apt-get update && apt-get install wine32 # add sudo to each if needed
# switch all of the following to their "-posix" variants (interactively):
for pkg in i686-w64-mingw32-g++ i686-w64-mingw32-gcc i686-w64-mingw32-gfortran x86_64-w64-mingw32-g++ x86_64-w64-mingw32-gcc x86_64-w64-mingw32-gfortran; do
    sudo update-alternatives --config $pkg
done
```

**Mac'te**: XCode, XCode komut satırı araçlarını, X11'i (şimdi [XQuartz](https://www.xquartz.org/)), ve [MacPorts](https://www.macports.org/install.php) veya [Homebrew](https://brew.sh/) yükleyin. Ardından `port install wine wget mingw-w64` veya uygun olarak `brew install wine wget mingw-w64` komutunu çalıştırın.

**Sonra yapıyı çalıştırın:**

1. `git clone https://github.com/JuliaLang/julia.git julia-win32`
2. `cd julia-win32`
3. `echo override XC_HOST = i686-w64-mingw32 >> Make.user`
4. `yap`
5. `make win-extras` (Çalıştırmadan önce gerekli `make binary-dist`)
6. `make binary-dist` ardından `make exe` komutunu çalıştırarak Windows yükleyicisini oluşturun.
7. `julia-*.exe` yükleyicisini hedef makineye taşıyın

Eğer 64-bit Windows için inşa ediyorsanız, adımlar esasen aynıdır. Sadece `XC_HOST` içindeki `i686`'yı `x86_64` ile değiştirin. (Not: Mac'te, wine yalnızca 32-bit modda çalışır).

## Debugging a cross-compiled build under wine

Cross-compiled bir versiyonunu hata ayıklamanın en etkili yolu, bir Windows sürümü GDB'yi yüklemek ve bunu her zamanki gibi wine altında çalıştırmaktır. Mevcut önceden derlenmiş paketler [as part of the MSYS2 project](https://packages.msys2.org/) olarak bilinir. GDB paketinin yanı sıra python ve termcap paketlerine de ihtiyacınız olabilir. Son olarak, GDB'nin istemcisi komut satırından başlatıldığında çalışmayabilir. Bu, normal GDB çağrısına `wineconsole` ekleyerek aşılabilir.

## After compiling

Yukarıdaki seçeneklerden birini kullanarak derleme yapmak, temel bir Julia derlemesi oluşturur, ancak tam Julia ikili yükleyicisini çalıştırdığınızda dahil edilen bazı ekstra bileşenleri içermez. Bu bileşenlere ihtiyacınız varsa, en kolay yol, `make win-extras` komutunu takiben `make binary-dist` ve `make exe` komutlarını kullanarak yükleyiciyi kendiniz oluşturmaktır. Ardından, ortaya çıkan yükleyiciyi çalıştırın.

## Windows Build Debugging

### GDB hangs with Cygwin mintty

  * GDB'yi Windows konsolu (cmd) altında çalıştırın. GDB [may not function properly](https://www.cygwin.com/ml/cygwin/2009-02/msg00531.html) mintty altında Cygwin olmayan uygulamalarla birlikte çalıştırın. Gerekirse mintty'den Windows konsolunu başlatmak için `cmd /c start` komutunu kullanabilirsiniz.

### GDB not attaching to the right process

  * Windows görev yöneticisinden PID'yi veya `ps` komutundan `WINPID`'yi kullanın, unix tarzı komut satırı araçlarından (örneğin `pgrep`) PID yerine. Windows görev yöneticisinde varsayılan olarak gösterilmiyorsa PID sütununu eklemeniz gerekebilir.

### GDB not showing the right backtrace

  * Julia sürecine bağlanırken, GDB doğru iş parçacığına bağlanmayabilir. Tüm iş parçacıklarını göstermek için `info threads` komutunu kullanın ve iş parçacığını değiştirmek için `thread <threadno>` komutunu kullanın.
  * 32 bit bir GDB sürümünü, Julia'nın 32 bit derlemesini hata ayıklamak için kullanmayı veya 64 bit bir GDB sürümünü, Julia'nın 64 bit derlemesini hata ayıklamak için kullanmayı unutmayın.

### Build process is slow/eats memory/hangs my computer

  * Windows [Superfetch](https://en.wikipedia.org/wiki/Windows_Vista_I/O_technologies#SuperFetch) ve [Program Compatibility Assistant](https://blogs.msdn.com/b/cjacks/archive/2011/11/22/managing-the-windows-7-program-compatibility-assistant-pca.aspx) hizmetlerini devre dışı bırakın, çünkü [spurious interactions](https://cygwin.com/ml/cygwin/2011-12/msg00058.html) ile MinGW/Cygwin ile bilinir.

    Yukarıda belirtilen bağlantıda: `svchost` tarafından aşırı bellek kullanımı, Görev Yöneticisi'nde yüksek bellek kullanan `svchost.exe` işlemine tıklanarak ve `Hizmetlere Git` seçeneği seçilerek incelenebilir. Bir suçlu bulunana kadar çocuk hizmetlerini tek tek devre dışı bırakın.
  * [BLODA](https://cygwin.com/faq/faq.html#faq.using.bloda)'dan kaçının. [vmmap](https://technet.microsoft.com/en-us/sysinternals/dd535533.aspx) aracı, bu tür yazılım çatışmalarını tanımlamak için vazgeçilmezdir. Bash, mintty veya yapıyı sürdürmek için kullanılan başka bir sürekli işlem için yüklü DLL'lerin listesini incelemek üzere vmmap kullanın. Temelde *herhangi bir* DLL, Windows Sistem dizini dışında potansiyel BLODA'dır.
