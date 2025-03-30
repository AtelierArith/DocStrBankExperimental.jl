# Building Julia (Detailed)

## Downloading the Julia source code

방화벽 뒤에 있는 경우 `git` 프로토콜 대신 `https` 프로토콜을 사용해야 할 수 있습니다:

```sh
git config --global url."https://".insteadOf git://
```

시스템이 적절한 프록시 설정을 사용하도록 구성하는 것도 잊지 마세요. 예를 들어 `https_proxy` 및 `http_proxy` 변수를 설정하여 구성할 수 있습니다.

## Building Julia

처음 컴파일할 때, 빌드는 자동으로 미리 빌드된 [external dependencies](#Required-Build-Tools-and-External-Libraries)를 다운로드합니다. 모든 종속성을 직접 빌드하거나 빌드 과정 중 네트워크에 접근할 수 없는 시스템에서 빌드하는 경우, `Make.user`에 다음을 추가하세요:

```
USE_BINARYBUILDER=0
```

Julia를 빌드하려면 모든 종속성을 빌드할 경우 5GiB와 약 4GiB의 가상 메모리가 필요합니다.

병렬 빌드를 수행하려면 `make -j N`을 사용하고 최대 동시 프로세스 수를 지정하십시오. 빌드의 기본값이 작동하지 않거나 특정 make 매개변수를 설정해야 하는 경우, 이를 `Make.user`에 저장하고 파일을 Julia 소스의 루트에 배치할 수 있습니다. 빌드는 자동으로 `Make.user`의 존재를 확인하고 존재하는 경우 이를 사용합니다.

Julia의 외부 빌드를 생성하려면 명령줄에서 `make O=<build-directory> configure`를 지정하면 됩니다. 이렇게 하면 지정된 디렉토리에 Julia를 빌드하는 데 필요한 모든 Makefile이 포함된 디렉토리 미러가 생성됩니다. 이러한 빌드는 Julia의 소스 파일과 `deps/srccache`를 공유합니다. 각 외부 빌드 디렉토리는 최상위 폴더의 전역 `Make.user` 파일을 재정의하기 위해 자체 `Make.user` 파일을 가질 수 있습니다.

모든 것이 올바르게 작동하면 Julia 배너와 평가를 위해 표현식을 입력할 수 있는 대화형 프롬프트가 표시됩니다. (라이브러리와 관련된 오류는 PATH에 오래되었거나 호환되지 않는 라이브러리가 있을 수 있습니다. 이 경우 `julia` 디렉토리를 PATH에서 더 앞쪽으로 이동해 보십시오). 위의 대부분의 지침은 유닉스 시스템에 적용된다는 점에 유의하십시오.

어디서든 줄리아를 실행하려면 다음과 같이 할 수 있습니다:

  * 별칭을 추가하세요 (bash에서: `echo "alias julia='/path/to/install/folder/bin/julia'" >> ~/.bashrc && source ~/.bashrc`), 또는
  * `julia` 디렉토리에 있는 `julia` 실행 파일에 대한 심볼릭 링크를 `/usr/local/bin` (또는 경로에 이미 있는 적절한 디렉토리)로 추가하세요.
  * `julia` 디렉토리를 이 셸 세션의 실행 파일 경로에 추가하세요 (in `bash`: `export PATH="$(pwd):$PATH"` ; in `csh` 또는 `tcsh`:

`set path= ( $path $cwd )` ), 또는

  * `julia` 디렉토리를 실행 파일 경로에 영구적으로 추가하세요 (예: `.bash_profile`에서), 또는
  * `Make.user`에 `prefix=/path/to/install/folder`를 작성한 후 `make install`을 실행하세요. 이 폴더에 이미 설치된 Julia 버전이 있다면, `make install`을 실행하기 전에 삭제해야 합니다.

`Make.inc` 파일의 시작 부분에 Julia 빌드를 제어하기 위해 설정할 수 있는 몇 가지 옵션이 나열되고 문서화되어 있지만, 이 목적을 위해 해당 파일을 수정해서는 안 되며 대신 `Make.user`를 사용해야 합니다.

줄리아의 Makefile은 변수의 값을 출력하기 위한 편리한 자동 규칙인 `print-<VARNAME>`을 정의합니다. 여기서 `<VARNAME>`은 출력할 변수의 이름으로 대체됩니다. 예를 들어

```console
$ make print-JULIA_PRECOMPILE
JULIA_PRECOMPILE=1
```

이 규칙들은 디버깅 목적으로 유용합니다.

이제 다음과 같이 Julia를 실행할 수 있어야 합니다:

```
julia
```

Linux, macOS 또는 Windows에서 배포할 Julia 패키지를 구축하는 경우, [distributing.md](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/distributing.md)의 자세한 노트를 확인하세요.

## Updating an existing source tree

이전에 `git clone`을 사용하여 `julia`를 다운로드한 경우, 새로 시작하는 대신 `git pull`을 사용하여 기존 소스 트리를 업데이트할 수 있습니다:

```sh
cd julia
git pull && make
```

업스트림 업데이트와 충돌할 수 있는 소스 트리에 변경 사항이 없다고 가정할 때, 이러한 명령은 최신 버전으로 업데이트하기 위한 빌드를 트리거합니다.

## General troubleshooting

1. 시간이 지나면서 기본 라이브러리에 충분한 변경 사항이 축적되어 시스템 이미지 빌드의 부트스트래핑 프로세스가 실패할 수 있습니다. 이 경우 빌드는 다음과 같은 오류로 실패할 수 있습니다.

    ```sh
     *** This error is usually fixed by running 'make clean'. If the error persists, try 'make cleanall' ***
    ```

    설명한 대로, `make clean && make`를 실행하는 것으로 보통 충분합니다. 가끔은 `make cleanall`로 더 강력한 정리가 필요합니다.
2. 새로운 외부 의존성 버전이 도입될 수 있으며, 이는 때때로 이전 버전의 기존 빌드와 충돌을 일으킬 수 있습니다.

    a. 특별한 `make` 타겟이 존재하여 의존성의 기존 빌드를 지우는 데 도움을 줍니다. 예를 들어, `make -C deps clean-llvm`은 기존의 `llvm` 빌드를 정리하여 다음 번 `make`가 호출될 때 `llvm`이 다운로드된 소스 배포판에서 다시 빌드되도록 합니다. `make -C deps distclean-llvm`은 더 강력한 지우기로, 다운로드된 소스 배포판도 삭제하여 다음 번 `make`가 호출될 때 새로운 소스 배포판이 다운로드되고 새로운 패치가 적용되도록 합니다.

    b. `julia`와 그 모든 의존성의 기존 바이너리를 삭제하려면, *소스 트리*에서 `./usr` 디렉토리를 삭제하십시오.
3. 최근에 macOS를 업데이트했다면, `xcode-select --install`을 실행하여 명령줄 도구를 업데이트해야 합니다. 그렇지 않으면 `ld: library not found for -lcrt1.10.6.o`와 같은 헤더 및 라이브러리가 누락된 오류가 발생할 수 있습니다.
4. 소스 디렉토리를 이동한 경우, `CMake Error: The current CMakeCache.txt directory ... is different than the directory ... where CMakeCache.txt was created.`와 같은 오류가 발생할 수 있습니다. 이 경우, `deps` 아래의 문제 있는 종속성을 삭제할 수 있습니다.
5. 극단적인 경우에는 소스 트리를 원래 상태로 재설정하고 싶을 수 있습니다. 다음의 git 명령어가 도움이 될 수 있습니다:

    ```sh
     git reset --hard #Forcibly remove any changes to any files under version control
     git clean -x -f -d #Forcibly remove any file or directory not under version control
    ```

    *작업을 잃지 않으려면, 이 명령어들이 무엇을 하는지 알고 실행하세요. `git`은 이러한 변경 사항을 되돌릴 수 없습니다!*

## Platform-Specific Notes

다양한 운영 체제에 대한 노트:

  * [Linux](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/linux.md)
  * [macOS](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/macos.md)
  * [Windows](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/windows.md)
  * [FreeBSD](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/freebsd.md)

다양한 아키텍처에 대한 노트:

  * [ARM](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/arm.md)

## Required Build Tools and External Libraries

Julia를 빌드하려면 다음 소프트웨어가 설치되어 있어야 합니다:

  * **[GNU make]**                — 의존성 빌드.
  * **[gcc & g++][gcc]** (>= 7.1) 또는 **[Clang][clang]** (>= 5.0, Apple Clang의 경우 >= 9.3) — C, C++ 컴파일 및 링크.
  * **[libatomic][gcc]**          — **[gcc]**에서 제공되며 원자적 작업을 지원하는 데 필요합니다.
  * **[python]** (>=2.7)          — LLVM을 빌드하는 데 필요합니다.
  * **[gfortran]**                — 포트란 라이브러리 컴파일 및 링크.
  * **[perl]**                    — 라이브러리의 헤더 파일 전처리.
  * **[wget]**, **[curl]**, 또는 **[fetch]** (FreeBSD) — 외부 라이브러리를 자동으로 다운로드합니다.
  * **[m4]**                      — GMP를 빌드하는 데 필요합니다.
  * **[awk]**                     — Makefile을 위한 도우미 도구.
  * **[패치]**                   — 소스 코드를 수정하기 위해.
  * **[cmake]** (>= 3.4.3)        — `libgit2`를 빌드하는 데 필요합니다.
  * **[pkg-config]**              — `libgit2`를 올바르게 빌드하는 데 필요하며, 특히 프록시 지원을 위해 필요합니다.
  * **[파워셸]** (>= 3.0)     — Windows에서만 필요합니다.
  * **[which]**                   — 빌드 종속성을 확인하는 데 필요합니다.

Debian 기반 배포판(예: Ubuntu)에서는 `apt-get`을 사용하여 쉽게 설치할 수 있습니다:

```
sudo apt-get install build-essential libatomic1 python gfortran perl wget m4 cmake pkg-config curl
```

줄리아는 다음과 같은 외부 라이브러리를 사용하며, 이 라이브러리는 자동으로 다운로드되거나(몇 가지 경우에는 줄리아 소스 리포지토리에 포함되어) `make`를 처음 실행할 때 소스에서 컴파일됩니다. 줄리아가 사용하는 이러한 라이브러리의 특정 버전 번호는 [`deps/$(libname).version`](https://github.com/JuliaLang/julia/blob/master/deps/)에 나열되어 있습니다:

  * **[LLVM]** (15.0 + [patches](https://github.com/JuliaLang/llvm-project/tree/julia-release/15.x)) — 컴파일러 인프라스트럭처 (자세한 내용은 [note below](#llvm)를 참조하십시오).
  * **[FemtoLisp]**            — 줄리아 소스와 함께 패키징되었으며, 컴파일러 프론트엔드를 구현하는 데 사용됩니다.
  * **[libuv]**  (커스텀 포크) — 이식 가능하고, 고성능의 이벤트 기반 I/O 라이브러리.
  * **[OpenLibm]**             — 기본 수학 함수를 포함하는 휴대용 libm 라이브러리.
  * **[DSFMT]**                — 빠른 Mersenne Twister 의사 난수 생성기 라이브러리.
  * **[OpenBLAS]**             — 빠르고, 개방적이며 유지 관리되는 [기본 선형 대수 서브프로그램 (BLAS)]
  * **[LAPACK]**               — 동시 선형 방정식 시스템을 해결하고, 선형 방정식 시스템의 최소 제곱 해, 고유값 문제 및 특이값 문제를 해결하기 위한 선형 대수 루틴 라이브러리.
  * **[MKL]** (선택 사항) – OpenBLAS와 LAPACK는 Intel의 MKL 라이브러리로 대체될 수 있습니다.
  * **[SuiteSparse]**          — 희소 행렬을 위한 선형 대수 루틴 라이브러리.
  * **[PCRE]**                 — 펄 호환 정규 표현식 라이브러리.
  * **[GMP]**                  — GNU 다중 정밀도 산술 라이브러리, `BigInt` 지원에 필요합니다.
  * **[MPFR]**                 — GNU 다중 정밀도 부동 소수점 라이브러리, 임의 정밀도 부동 소수점(`BigFloat`) 지원에 필요합니다.
  * **[libgit2]**              — 줄리아의 패키지 관리자가 사용하는 Git 링크 가능 라이브러리.
  * **[curl]**                 — libcurl은 다운로드 및 프록시 지원을 제공합니다.
  * **[libssh2]**              — SSH 전송을 위한 라이브러리로, SSH 원격이 있는 패키지에 대해 libgit2에서 사용됩니다.
  * **[mbedtls]**              — 암호화 및 전송 계층 보안을 위해 사용되는 라이브러리, libssh2에서 사용됨
  * **[utf8proc]**             — UTF-8로 인코딩된 유니코드 문자열을 처리하기 위한 라이브러리.
  * **[LLVM libunwind]** — LLVM의 [libunwind] 포크로, 프로그램의 호출 체인을 결정하는 라이브러리입니다.
  * **[ITTAPI]**               — 인텔의 계측 및 추적 기술과 즉시 사용 가능한 API.

[GNU make]:     https://www.gnu.org/software/make [patch]:        https://www.gnu.org/software/patch [wget]:         https://www.gnu.org/software/wget [m4]:           https://www.gnu.org/software/m4 [awk]:          https://www.gnu.org/software/gawk [gcc]:          https://gcc.gnu.org [clang]:        https://clang.llvm.org [python]:       https://www.python.org/ [gfortran]:     https://gcc.gnu.org/fortran/ [curl]:         https://curl.haxx.se [fetch]:        https://www.freebsd.org/cgi/man.cgi?fetch(1) [perl]:         https://www.perl.org [cmake]:        https://www.cmake.org [OpenLibm]:     https://github.com/JuliaLang/openlibm [DSFMT]:        https://github.com/MersenneTwister-Lab/dSFMT [OpenBLAS]:     https://github.com/xianyi/OpenBLAS [LAPACK]:       https://www.netlib.org/lapack [MKL]:          https://software.intel.com/en-us/articles/intel-mkl [SuiteSparse]:  https://people.engr.tamu.edu/davis/suitesparse.html [PCRE]:         https://www.pcre.org [LLVM]:         https://www.llvm.org [LLVM libunwind]: https://github.com/llvm/llvm-project/tree/main/libunwind [FemtoLisp]:    https://github.com/JeffBezanson/femtolisp [GMP]:          https://gmplib.org [MPFR]:         https://www.mpfr.org [libuv]:        https://github.com/JuliaLang/libuv [libgit2]:      https://libgit2.org/ [utf8proc]:     https://julialang.org/utf8proc/ [libunwind]:    https://www.nongnu.org/libunwind [libssh2]:      https://www.libssh2.org [mbedtls]:      https://tls.mbed.org/ [pkg-config]:   https://www.freedesktop.org/wiki/Software/pkg-config/ [powershell]:   https://docs.microsoft.com/en-us/powershell/scripting/wmf/overview [which]:        https://carlowood.github.io/which/ [ITTAPI]:       https://github.com/intel/ittapi

## Build dependencies

시스템에 이러한 패키지 중 하나 이상이 이미 설치되어 있는 경우, `USE_SYSTEM_...=1`을 `make`에 전달하거나 `Make.user`에 해당 줄을 추가하여 Julia가 이러한 라이브러리의 중복 컴파일을 방지할 수 있습니다. 가능한 플래그의 전체 목록은 `Make.inc`에서 확인할 수 있습니다.

이 절차는 공식적으로 지원되지 않으며, 의존성의 설치 및 버전 관리에 추가적인 변동성을 도입하므로 시스템 패키지 유지 관리자를 위해서만 권장됩니다. 적절한 패키지가 설치되었는지 확인하기 위한 추가 검사가 이루어지지 않기 때문에 예기치 않은 컴파일 오류가 발생할 수 있습니다.

### LLVM

가장 복잡한 의존성은 LLVM으로, 이를 위해 추가적인 패치가 필요합니다 (LLVM은 이전 버전과 호환되지 않습니다).

Julia를 LLVM과 함께 패키징하기 위해서는 다음 중 하나를 권장합니다:

  * Julia 패키지 내에 Julia 전용 LLVM 라이브러리를 번들링하거나
  * 배포의 LLVM 패키지에 패치를 추가합니다.

      * 전체 패치 목록은 [Github](https://github.com/JuliaLang/llvm-project)에서 확인할 수 있으며, `julia-release/15.x` 브랜치를 참조하세요.
      * 유일한 Julia 전용 패치는 lib 이름 변경(`llvm7-symver-jlprefix.patch`)으로, 이는 시스템 LLVM에 적용되어서는 *안 됩니다*.
      * 남은 패치는 모두 업스트림 버그 수정이며, 업스트림 LLVM에 기여되었습니다.

패치되지 않았거나 다른 버전의 LLVM을 사용하면 오류 및/또는 성능 저하가 발생할 수 있습니다. 다음 옵션을 사용하여 원격 Git 리포지토리에서 다른 버전의 LLVM을 빌드할 수 있습니다 `Make.user` 파일:

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

다양한 빌드 단계는 특정 파일에 의해 제어됩니다:

  * `deps/llvm.version` : 새로운 버전을 체크아웃하기 위해 터치하거나 변경, `make get-llvm check-llvm`
  * `deps/srccache/llvm/source-extracted` : `make extract-llvm`의 결과
  * `deps/llvm/build_Release*/build-configured` : `make configure-llvm`의 결과
  * `deps/llvm/build_Release*/build-configured` : `make compile-llvm`의 결과
  * `usr-staging/llvm/build_Release*.tgz` : `make stage-llvm`의 결과 ( `make reinstall-llvm`로 재생성)
  * `usr/manifest/llvm` : `make install-llvm`의 결과 ( `make uninstall-llvm`로 재생성)
  * `make version-check-llvm` : 사용자가 로컬 수정 사항이 있는 경우 경고하기 위해 매번 실행됩니다.

줄리아는 최신 LLVM 버전으로 빌드할 수 있지만, 이에 대한 지원은 실험적이며 패키징에 적합하지 않다고 간주해야 합니다.

### libuv

Julia는 libuv의 사용자 정의 포크를 사용합니다. 이는 작은 의존성이며, Julia와 동일한 패키지에 안전하게 번들될 수 있으며, 시스템 라이브러리와 충돌하지 않습니다. Julia 빌드는 시스템 libuv를 사용하려고 해서는 안 됩니다.

### BLAS and LAPACK

고성능 수치 언어인 Julia는 OpenBLAS 또는 ATLAS와 같은 다중 스레드 BLAS 및 LAPACK에 연결되어야 하며, 이는 일부 시스템에서 기본값일 수 있는 참조 `libblas` 구현보다 훨씬 더 나은 성능을 제공합니다.

## Source distributions of releases

각 프리릴리스 및 릴리스의 Julia는 "전체" 소스 배포판과 "경량" 소스 배포판을 가지고 있습니다.

전체 소스 배포판에는 Julia의 소스 코드와 모든 종속성이 포함되어 있어 인터넷 연결 없이 소스에서 빌드할 수 있습니다. 경량 소스 배포판에는 종속성의 소스 코드가 포함되어 있지 않습니다.

예를 들어, `julia-1.0.0.tar.gz`는 Julia의 `v1.0.0` 릴리스를 위한 경량 소스 배포판이며, `julia-1.0.0-full.tar.gz`는 전체 소스 배포판입니다.

## Building Julia from source with a Git checkout of a stdlib

Julia를 소스에서 빌드하고 stdlib의 Git 체크아웃을 사용해야 하는 경우, Julia를 빌드할 때 `make DEPS_GIT=NAME_OF_STDLIB`를 사용하세요.

예를 들어, Pkg의 Git 체크아웃으로부터 소스에서 Julia를 빌드해야 하는 경우, Julia를 빌드할 때 `make DEPS_GIT=Pkg`를 사용하세요. `Pkg` 리포지토리는 `stdlib/Pkg`에 있으며, 처음에는 분리된 `HEAD`로 생성됩니다. 기존의 Julia 리포지토리에서 이 작업을 수행하는 경우, 사전에 `make clean`을 실행해야 할 수도 있습니다.

만약 여러 개의 표준 라이브러리(stdlib)의 Git 체크아웃으로부터 Julia를 소스에서 빌드해야 한다면, `DEPS_GIT`는 표준 라이브러리 이름의 공백으로 구분된 목록이어야 합니다. 예를 들어, Pkg, Tar 및 Downloads의 Git 체크아웃으로부터 Julia를 소스에서 빌드해야 한다면, Julia를 빌드할 때 `make DEPS_GIT='Pkg Tar Downloads'`를 사용하세요.

## Building an "assert build" of Julia

"assert build"는 `FORCE_ASSERTIONS=1`과 `LLVM_ASSERTIONS=1`이 모두 설정된 빌드를 의미합니다. assert build를 만들기 위해서는 `Make.user` 파일에 다음 두 변수를 모두 정의해야 합니다:

```
FORCE_ASSERTIONS=1
LLVM_ASSERTIONS=1
```

assert 빌드의 Julia는 일반(비 assert) 빌드보다 느릴 것임을 유의하시기 바랍니다.

## Building 32-bit Julia on a 64-bit machine

가끔 32비트 아키텍처에 특정한 버그가 발생할 수 있으며, 이럴 때 문제를 로컬 머신에서 디버깅할 수 있는 것이 유용합니다. 대부분의 현대 64비트 시스템은 32비트 프로그램을 실행하는 것을 지원하므로, Julia를 소스에서 다시 컴파일할 필요가 없다면(예: C 코드를 건드리지 않고 32비트 Julia의 동작을 주로 검사해야 하는 경우), [official downloads page](https://julialang.org/downloads/)에서 얻을 수 있는 시스템에 맞는 32비트 빌드의 Julia를 사용할 수 있습니다. 그러나 소스에서 Julia를 다시 컴파일해야 하는 경우, 32비트 시스템의 Docker 컨테이너를 사용하는 옵션이 있습니다. 적어도 지금은 [ubuntu 32-bit docker images](https://hub.docker.com/r/i386/ubuntu)를 사용하여 32비트 버전의 Julia를 빌드하는 것이 비교적 간단합니다. 간단히 말해, `docker`를 설정한 후 필요한 단계는 다음과 같습니다:

```sh
$ docker pull i386/ubuntu
$ docker run --platform i386 -i -t i386/ubuntu /bin/bash
```

이 시점에서 당신은 32비트 머신 콘솔에 있어야 합니다 (note that `uname` reports the host architecture, so will still say 64-bit, but this will not affect the Julia build). 패키지를 추가하고 코드를 컴파일할 수 있습니다; `exit`를 입력하면 모든 변경 사항이 사라지므로, 단일 세션에서 분석을 마치거나 환경을 설정하는 데 사용할 수 있는 복사/붙여넣기 가능한 스크립트를 설정하는 것이 좋습니다.

이 시점부터, 당신은 다음을 해야 합니다.

```sh
# apt update
```

(참고: `sudo`는 설치되어 있지 않지만, `root`로 실행 중이므로 모든 명령에서 `sudo`를 생략할 수 있습니다.)

그런 다음 모든 [build dependencies](#required-build-tools-and-external-libraries), 선택한 콘솔 기반 편집기, `git`, 및 필요한 모든 것을 추가하세요 (예: `gdb`, `rr` 등). 작업할 디렉토리를 선택하고 `git clone`을 사용하여 Julia를 복제한 후, 디버깅할 브랜치를 체크아웃하고 일반적으로 Julia를 빌드하세요.

## Update the version number of a dependency

두 가지 유형의 빌드가 있습니다.

1. 모든 것(`deps/` 및 `src/`)을 소스 코드에서 빌드합니다. (`Make.user`에 `USE_BINARYBUILDER=0`을 추가하세요. [Building Julia](#building-julia)을 참조하세요.)
2. 소스에서 빌드하기 (`src/`) 및 미리 컴파일된 종속성 사용 (기본값)

`deps/`의 종속성 버전 번호를 업데이트하려는 경우 다음 체크리스트를 사용할 수 있습니다:

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

노트:

  * 특정 종속성에 따라 체크리스트의 일부 항목이 존재하지 않을 수 있습니다.
  * 체크섬 파일은 **접미사가 없는 단일 파일**일 수도 있고, **두 개의 파일을 포함하는 폴더**일 수도 있습니다.

### Example: `OpenLibm`

1. `deps/openlibm.version`의 버전 번호를 업데이트하세요.

      * `OPENLIBM_VER := 0.X.Y`
      * `OPENLIBM_BRANCH = v0.X.Y`
      * `OPENLIBM_SHA1 = new-sha1-hash`
2. `stdlib/OpenLibm_jll/Project.toml`에서 버전 번호 업데이트

      * `version = "0.X.Y+0"`
3. `deps/checksums/openlibm`의 체크섬을 업데이트합니다.

      * `make -f contrib/refresh_checksums.mk openlibm`
4. `deps/patches/openlibm-*.patch` 파일이 존재하는지 확인하세요.

      * 패치가 존재하지 않으면 건너뜁니다.
      * 패치가 존재하는 경우, 새로운 버전에 병합되었는지 확인하고 제거해야 하는지 확인하십시오. 패치를 삭제할 때는 해당 Makefile 파일(`deps/openlibm.mk`)을 수정하는 것을 잊지 마십시오.
