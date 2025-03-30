# Windows

이 파일은 Windows에서 Julia를 설치하거나 빌드하고 사용하는 방법을 설명합니다.

더 일반적인 Julia에 대한 정보는 [main README](https://github.com/JuliaLang/julia/blob/master/README.md) 또는 [documentation](https://docs.julialang.org)를 참조하십시오.

## General Information for Windows

우리는 특히 [Microsoft Store](https://aka.ms/terminal)에서 설치할 수 있는 Windows Terminal을 사용하여 현대적인 터미널 애플리케이션에서 Julia를 실행할 것을 강력히 권장합니다.

### Line endings

줄리아는 이진 모드 파일만 사용합니다. 많은 다른 Windows 프로그램과 달리, 파일에 `\n`을 쓰면 파일에 `\n`이 들어가고, 다른 비트 패턴이 들어가지 않습니다. 이는 다른 운영 체제에서 나타나는 동작과 일치합니다. Windows용 Git을 설치한 경우, 시스템 Git을 동일한 규칙을 사용하도록 설정하는 것이 권장되지만 필수는 아닙니다:

```sh
git config --global core.eol lf
git config --global core.autocrlf input
```

또는 `%USERPROFILE%\.gitconfig` 파일을 편집하고 다음 줄을 추가/편집하세요:

```
[core]
    eol = lf
    autocrlf = input
```

## Binary distribution

Windows에서 이진 배포 설치 노트에 대한 지침은 [https://julialang.org/downloads/platform/#windows](https://julialang.org/downloads/platform/#windows)를 참조하십시오.

## Source distribution

### Cygwin-to-MinGW cross-compiling

Windows에서 소스에서 Julia를 컴파일하는 권장 방법은 [Cygwin](https://www.cygwin.com)에서 크로스 컴파일하는 것이며, Cygwin의 패키지 관리자를 통해 사용할 수 있는 MinGW-w64 컴파일러 버전을 사용합니다.

1. [32 bit](https://cygwin.com/setup-x86.exe) 또는 [64 bit](https://cygwin.com/setup-x86_64.exe)에 대한 Cygwin 설치 프로그램을 다운로드하고 실행하십시오. 32비트 또는 64비트 Cygwin에서 32비트 또는 64비트 Julia를 컴파일할 수 있습니다. 64비트 Cygwin은 약간 더 적은 수의 패키지를 제공하지만 종종 더 최신의 패키지를 제공합니다.

    *고급*: 다음 명령어를 실행하여 2-4단계를 건너뛸 수 있습니다:

    ```sh
    setup-x86_64.exe -s <url> -q -P cmake,gcc-g++,git,make,patch,curl,m4,python3,p7zip,mingw64-i686-gcc-g++,mingw64-i686-gcc-fortran,mingw64-x86_64-gcc-g++,mingw64-x86_64-gcc-fortran
    ```

    replacing `<url>` with a site from [https://cygwin.com/mirrors.html](https://cygwin.com/mirrors.html) or run setup manually first and select a mirror.
2. 설치 위치와 다운로드할 미러를 선택하세요.
3. *패키지 선택* 단계에서 다음을 선택하세요:

    1. *Devel* 카테고리에서: `cmake`, `gcc-g++`, `git`, `make`, `patch`
    2. *Net* 카테고리에서: `curl`
    3. *인터프리터* (또는 *파이썬*) 카테고리: `m4`, `python3`
    4. *아카이브* 카테고리에서: `p7zip`
    5. 32비트 Julia 및 *Devel* 카테고리에서: `mingw64-i686-gcc-g++` 및 `mingw64-i686-gcc-fortran`
    6. 64비트 Julia 및 *Devel* 카테고리에서: `mingw64-x86_64-gcc-g++` 및 `mingw64-x86_64-gcc-fortran`
4. Cygwin 설치가 완료되면 설치된 바로가기 *'Cygwin Terminal'* 또는 *'Cygwin64 Terminal'*에서 시작하십시오.
5. 소스에서 Julia와 그 의존성을 빌드합니다:

    1. Julia 소스 가져오기

        ```sh
        git clone https://github.com/JuliaLang/julia.git
        cd julia
        ```

        팁: git에서 `error: cannot fork() for fetch-pack: Resource temporarily unavailable` 오류가 발생하면, `~/.bashrc`에 `alias git="env PATH=/usr/bin git"`를 추가하고 Cygwin을 재시작하세요.
    2. `Make.user` 파일에서 MinGW-w64 크로스 컴파일을 나타내기 위해 `XC_HOST` 변수를 설정하세요.

        ```sh
        echo 'XC_HOST = i686-w64-mingw32' > Make.user     # for 32 bit Julia
        # or
        echo 'XC_HOST = x86_64-w64-mingw32' > Make.user   # for 64 bit Julia
        ```
    3. 빌드 시작

        ```sh
        make -j 4       # Adjust the number of threads (4) to match your build environment.
        make -j 4 debug # This builds julia-debug.exe
        ```
6. Julia 실행 파일을 직접 사용하여 Julia 실행하기

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

[MSYS2](https://www.msys2.org/)는 Windows용 소프트웨어 배포 및 빌드 환경입니다.

참고: MSYS2는 **64비트** Windows 7 이상이 필요합니다.

1. MSYS2를 설치하고 구성합니다.

    1. 최신 설치 프로그램을 다운로드하고 실행하십시오 [64-bit](https://github.com/msys2/msys2-installer/releases/latest) 배포판. 설치 프로그램의 이름은 `msys2-x86_64-yyyymmdd.exe`와 비슷할 것입니다.
    2. MSYS2 셸을 엽니다. 패키지 데이터베이스와 기본 패키지를 업데이트합니다:

        `pacman -Syu`
    3. MSYS2를 종료하고 다시 시작합니다. 나머지 기본 패키지를 업데이트합니다:

        `pacman -Syu`
    4. 그런 다음 줄리아를 빌드하는 데 필요한 도구를 설치하십시오:

        `pacman -S cmake diffutils git m4 make patch tar p7zip curl python`

        64비트 Julia의 경우, x86_64 버전을 설치하세요:

        `pacman -S mingw-w64-x86_64-gcc`

        32비트 Julia를 설치하려면 i686 버전을 설치하세요:

        `pacman -S mingw-w64-i686-gcc`
    5. MSYS2의 구성이 완료되었습니다. 이제 MSYS2 셸에서 `exit`를 입력하세요.
2. 사전 빌드 종속성과 함께 Julia 및 그 종속성을 빌드합니다.

    1. 새로운 [**MINGW64/MINGW32 shell**](https://www.msys2.org/docs/environments/#overview)를 엽니다. 현재 mingw32와 mingw64를 동시에 사용할 수 없으므로, x86_64 및 i686 버전을 빌드하려면 각 환경에서 별도로 빌드해야 합니다.
    2. 줄리아 소스를 클론하세요:

        `git clone https://github.com/JuliaLang/julia.git  cd julia`
    3. 빌드 시작

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

Linux, Mac 또는 Windows Subsystem for Linux (WSL)에서 Windows 버전의 Julia를 빌드하기 위해 MinGW-w64 크로스 컴파일러를 사용할 수도 있습니다.

먼저, 시스템에 필요한 종속성이 설치되어 있는지 확인해야 합니다. 우리는 wine (>=1.7.5), 시스템 컴파일러, 그리고 몇 가지 다운로드 도구가 필요합니다. 참고: WSL을 사용할 경우 Cygwin 설치가 이 방법에 간섭할 수 있습니다.

**우분투에서** (다른 리눅스 시스템에서는 의존성 이름이 비슷할 가능성이 높습니다):

```sh
apt-get install wine-stable gcc wget p7zip-full winbind mingw-w64 gfortran-mingw-w64
dpkg --add-architecture i386 && apt-get update && apt-get install wine32 # add sudo to each if needed
# switch all of the following to their "-posix" variants (interactively):
for pkg in i686-w64-mingw32-g++ i686-w64-mingw32-gcc i686-w64-mingw32-gfortran x86_64-w64-mingw32-g++ x86_64-w64-mingw32-gcc x86_64-w64-mingw32-gfortran; do
    sudo update-alternatives --config $pkg
done
```

**맥에서**: XCode, XCode 명령줄 도구, X11(현재 [XQuartz](https://www.xquartz.org/)), 및 [MacPorts](https://www.macports.org/install.php) 또는 [Homebrew](https://brew.sh/)를 설치합니다. 그런 다음 `port install wine wget mingw-w64` 또는 `brew install wine wget mingw-w64`를 적절히 실행합니다.

**그런 다음 빌드를 실행하세요:**

1. `git clone https://github.com/JuliaLang/julia.git julia-win32`
2. `cd julia-win32`
3. `echo override XC_HOST = i686-w64-mingw32 >> Make.user`
4. `만들다`
5. `make win-extras` (이것은 `make binary-dist`를 실행하기 전에 필요합니다)
6. `make binary-dist` 다음에 `make exe`를 실행하여 Windows 설치 프로그램을 생성합니다.
7. `julia-*.exe` 설치 프로그램을 대상 머신으로 이동합니다.

64비트 Windows용으로 빌드하는 경우, 단계는 본질적으로 동일합니다. `XC_HOST`의 `i686`을 `x86_64`로 교체하기만 하면 됩니다. (참고: Mac에서는 wine이 32비트 모드에서만 실행됩니다).

## Debugging a cross-compiled build under wine

크로스 컴파일 호스트에서 크로스 컴파일된 Julia 버전을 디버깅하는 가장 효과적인 방법은 Windows 버전의 GDB를 설치하고 일반적으로 wine에서 실행하는 것입니다. 사용 가능한 미리 빌드된 패키지 [as part of the MSYS2 project](https://packages.msys2.org/)는 작동하는 것으로 알려져 있습니다. GDB 패키지 외에도 python 및 termcap 패키지가 필요할 수 있습니다. 마지막으로, GDB의 프롬프트는 명령줄에서 실행할 때 작동하지 않을 수 있습니다. 이는 일반 GDB 호출 앞에 `wineconsole`을 추가하여 우회할 수 있습니다.

## After compiling

위의 옵션 중 하나를 사용하여 컴파일하면 기본 Julia 빌드가 생성되지만, 전체 Julia 바이너리 설치 프로그램을 실행할 경우 포함되는 추가 구성 요소는 포함되지 않습니다. 이러한 구성 요소가 필요하다면, 가장 쉬운 방법은 `make win-extras`를 실행한 후 `make binary-dist`와 `make exe`를 사용하여 설치 프로그램을 직접 빌드하는 것입니다. 그런 다음 생성된 설치 프로그램을 실행하십시오.

## Windows Build Debugging

### GDB hangs with Cygwin mintty

  * Windows 콘솔(cmd)에서 GDB를 실행하세요. GDB [may not function properly](https://www.cygwin.com/ml/cygwin/2009-02/msg00531.html)를 mintty에서 비-Cygwin 애플리케이션과 함께 사용하세요. 필요하다면 `cmd /c start`를 사용하여 mintty에서 Windows 콘솔을 시작할 수 있습니다.

### GDB not attaching to the right process

  * Windows 작업 관리자에서 PID를 사용하거나 `ps` 명령의 `WINPID`를 사용하세요. Unix 스타일의 명령줄 도구(예: `pgrep`)에서 PID를 사용하는 대신에 사용해야 합니다. Windows 작업 관리자에서 기본적으로 표시되지 않는 경우 PID 열을 추가해야 할 수도 있습니다.

### GDB not showing the right backtrace

  * 줄리아 프로세스에 연결할 때, GDB가 올바른 스레드에 연결되지 않을 수 있습니다. `info threads` 명령어를 사용하여 모든 스레드를 표시하고, `thread <threadno>`를 사용하여 스레드를 전환하세요.
  * 32비트 빌드의 Julia를 디버깅하려면 32비트 버전의 GDB를 사용하고, 64비트 빌드의 Julia를 디버깅하려면 64비트 버전의 GDB를 사용해야 합니다.

### Build process is slow/eats memory/hangs my computer

  * Windows [Superfetch](https://en.wikipedia.org/wiki/Windows_Vista_I/O_technologies#SuperFetch) 및 [Program Compatibility Assistant](https://blogs.msdn.com/b/cjacks/archive/2011/11/22/managing-the-windows-7-program-compatibility-assistant-pca.aspx) 서비스를 비활성화하십시오. 이 서비스는 MinGW/Cygwin과 함께 [spurious interactions](https://cygwin.com/ml/cygwin/2011-12/msg00058.html)로 알려져 있습니다.

    위 링크에서 언급한 바와 같이: `svchost`의 과도한 메모리 사용은 작업 관리자에서 높은 메모리 사용량을 보이는 `svchost.exe` 프로세스를 클릭하고 `서비스로 이동`을 선택하여 조사할 수 있습니다. 문제의 원인을 찾을 때까지 자식 서비스를 하나씩 비활성화하십시오.
  * [BLODA](https://cygwin.com/faq/faq.html#faq.using.bloda)를 주의하세요. [vmmap](https://technet.microsoft.com/en-us/sysinternals/dd535533.aspx) 도구는 이러한 소프트웨어 충돌을 식별하는 데 필수적입니다. vmmap을 사용하여 bash, mintty 또는 빌드를 구동하는 데 사용되는 다른 지속적인 프로세스의 로드된 DLL 목록을 검사하세요. 본질적으로 Windows 시스템 디렉토리 외부의 *모든* DLL은 잠재적인 BLODA입니다.
