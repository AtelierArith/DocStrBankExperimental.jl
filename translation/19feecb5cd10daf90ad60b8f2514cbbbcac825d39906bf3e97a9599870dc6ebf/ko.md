# Sanitizer support

[Sanitizers](https://github.com/google/sanitizers)는 Julia의 내부 C/C++ 코드에서 특정 종류의 오류를 더 쉽게 감지할 수 있도록 사용자 정의 Julia 빌드에서 사용할 수 있습니다.

## Address Sanitizer: easy build

소스 체크아웃에서 Julia를 사용하여 Julia와 LLVM에서 주소 샌타이제이션을 지원하는 버전을 다음과 같이 빌드할 수 있어야 합니다:

```sh
$ mkdir /tmp/julia
$ contrib/asan/build.sh /tmp/julia/
```

여기서는 `/tmp/julia`를 빌드 디렉토리로 선택했지만, 원하는 다른 디렉토리를 선택할 수 있습니다. 빌드가 완료되면 `/tmp/julia/julia`로 테스트할 작업을 실행하세요. 메모리 버그는 오류를 초래할 것입니다.

사용자 정의 또는 추가 세부 정보가 필요한 경우 아래 문서를 참조하십시오.

## General considerations

Clang의 샌타이저를 사용하려면 명백히 Clang을 사용해야 합니다(`USECLANG=1`), 하지만 또 다른 문제가 있습니다: 대부분의 샌타이저는 호스트 컴파일러가 제공하는 런타임 라이브러리를 필요로 하며, Julia의 JIT에 의해 생성된 계측된 코드는 해당 라이브러리의 기능에 의존합니다. 이는 호스트 컴파일러의 LLVM 버전이 Julia 내에서 사용되는 LLVM 라이브러리의 버전과 일치해야 함을 의미합니다.

간단한 해결책은 일치하는 툴체인을 제공하기 위해 전용 빌드 폴더를 만드는 것입니다. `BUILD_LLVM_CLANG=1`로 빌드하면 됩니다. 그런 다음 `CC` 및 `CXX` 변수를 재정의하면서 `USECLANG=1`을 지정하여 다른 빌드 폴더에서 이 툴체인을 참조할 수 있습니다.

샌타이저는 `RTLD_DEEPBIND`를 사용하여 열리는 공유 라이브러리를 감지할 때 오류를 발생시킵니다 (참조: [google/sanitizers#611](https://github.com/google/sanitizers/issues/611)). 기본적으로 [libblastrampoline](https://github.com/staticfloat/libblastrampoline)는 `RTLD_DEEPBIND`를 사용하므로, 샌타이저를 사용할 때 환경 변수 `LBT_USE_RTLD_DEEPBIND=0`을 설정해야 합니다.

하나의 샌타이저를 사용하려면 `SANITIZE=1`을 설정한 다음 사용하려는 샌타이저에 대한 적절한 플래그를 설정하세요.

macOS에서는 작동하기 위해 추가 플래그가 필요할 수 있습니다. 전체적으로 다음과 같이 보일 수 있으며, 아래에 나열된 하나 이상의 `SANITIZE_*` 플래그가 추가될 수 있습니다:

```
make -C deps USE_BINARYBUILDER_LLVM=0 LLVM_VER=svn stage-llvm

make -C src SANITIZE=1 USECLANG=1 \
    CC=~+/deps/scratch/llvm-svn/build_Release/bin/clang \
    CXX=~+/deps/scratch/llvm-svn/build_Release/bin/clang++ \
    CPPFLAGS="-isysroot $(xcode-select -p)/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk" \
    CXXFLAGS="-isystem $(xcode-select -p)/Toolchains/XcodeDefault.xctoolchain/usr/include/c++/v1"
```

(또는 이를 `Make.user`에 넣어두면 매번 기억할 필요가 없습니다).

## Address Sanitizer (ASAN)

메모리 버그를 감지하거나 디버깅하기 위해 Clang의 [address sanitizer (ASAN)](https://clang.llvm.org/docs/AddressSanitizer.html)를 사용할 수 있습니다. `SANITIZE_ADDRESS=1`로 컴파일하면 Julia 컴파일러와 그로 생성된 코드에 대해 ASAN을 활성화합니다. 또한 `LLVM_SANITIZE=1`을 지정하여 LLVM 라이브러리도 정리할 수 있습니다. 이러한 옵션은 높은 성능 및 메모리 비용이 발생한다는 점에 유의하세요. 예를 들어, Julia와 LLVM에 대해 ASAN을 사용하면 `testall1`이 8-10배 더 오랜 시간이 걸리고 메모리 사용량이 20배 증가합니다(아래 설명된 옵션을 사용하면 각각 3배 및 4배로 줄일 수 있습니다).

기본적으로, Julia는 신호 전달이 제대로 작동하기 위해 필요한 `allow_user_segv_handler=1` ASAN 플래그를 설정합니다. `ASAN_OPTIONS` 환경 플래그를 사용하여 다른 옵션을 정의할 수 있으며, 이 경우 앞서 언급한 기본 옵션을 반복해야 합니다. 예를 들어, `fast_unwind_on_malloc=0` 및 `malloc_context_size=2`를 지정하여 메모리 사용량을 줄일 수 있지만, 이는 백트레이스 정확도의 대가를 치르게 됩니다. 현재 Julia는 또한 `detect_leaks=0`을 설정하지만, 이는 향후 제거되어야 합니다.

### Example setup

#### Step 1: Install toolchain

`$TOOLCHAIN_WORKTREE`에서 Git worktree를 체크아웃(또는 트리 외부 빌드 디렉토리 생성)하고, `$TOOLCHAIN_WORKTREE/Make.user`에 다음과 같은 구성 파일을 생성합니다.

```
USE_BINARYBUILDER_LLVM=1
BUILD_LLVM_CLANG=1
```

실행:

```sh
cd $TOOLCHAIN_WORKTREE
make -C deps install-llvm install-clang install-llvm-tools
```

툴체인 바이너리를 `$TOOLCHAIN_WORKTREE/usr/tools`에 설치하려면

#### Step 2: Build Julia with ASAN

`$BUILD_WORKTREE`에서 Git 작업 트리를 체크아웃(또는 트리 외부 빌드 디렉토리 생성)하고 `$BUILD_WORKTREE/Make.user`에 구성 파일을 생성합니다.

```
TOOLCHAIN=$(TOOLCHAIN_WORKTREE)/usr/tools

# use our new toolchain
USECLANG=1
override CC=$(TOOLCHAIN)/clang
override CXX=$(TOOLCHAIN)/clang++
export ASAN_SYMBOLIZER_PATH=$(TOOLCHAIN)/llvm-symbolizer

USE_BINARYBUILDER_LLVM=1

override SANITIZE=1
override SANITIZE_ADDRESS=1

# make the GC use regular malloc/frees, which are hooked by ASAN
override WITH_GC_DEBUG_ENV=1

# default to a debug build for better line number reporting
override JULIA_BUILD_MODE=debug

# make ASAN consume less memory
export ASAN_OPTIONS=detect_leaks=0:fast_unwind_on_malloc=0:allow_user_segv_handler=1:malloc_context_size=2

JULIA_PRECOMPILE=1

# tell libblastrampoline to not use RTLD_DEEPBIND
export LBT_USE_RTLD_DEEPBIND=0
```

실행:

```sh
cd $BUILD_WORKTREE
make debug
```

`julia-debug`를 ASAN으로 빌드하려면.

## Memory Sanitizer (MSAN)

초기화되지 않은 메모리 사용을 감지하기 위해 Clang의 [memory sanitizer (MSAN)](https://clang.llvm.org/docs/MemorySanitizer.html)를 사용할 수 있으며, `SANITIZE_MEMORY=1`로 컴파일하면 됩니다.

## Thread Sanitizer (TSAN)

스레드 관련 문제와 데이터 경합을 디버깅하기 위해 Clang의 [thread sanitizer (TSAN)](https://clang.llvm.org/docs/ThreadSanitizer.html)를 사용할 수 있으며, `SANITIZE_THREAD=1`로 컴파일하면 됩니다.
