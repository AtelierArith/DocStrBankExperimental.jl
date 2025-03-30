# [Package Images](@id pkgimages)

Julia 패키지 이미지들은 Julia 패키지를 위한 객체(네이티브 코드) 캐시를 제공합니다. 이들은 Julia의 [system image](@ref dev-sysimg)와 유사하며, 많은 동일한 기능을 지원합니다. 사실, 기본 직렬화 형식은 동일하며, 시스템 이미지는 패키지 이미지가 구축되는 기본 이미지입니다.

## High-level overview

패키지 이미지는 코드와 데이터를 모두 포함하는 공유 라이브러리입니다. `.ji` 캐시 파일처럼, 패키지별로 생성됩니다. 데이터 섹션에는 패키지의 전역 데이터(전역 변수)와 패키지에서 정의된 메서드 및 유형에 대한 필요한 메타데이터가 포함되어 있습니다. 코드 섹션에는 줄리아의 LLVM 기반 컴파일러의 최종 출력을 캐시하는 네이티브 객체가 포함되어 있습니다.

명령줄 옵션 `--pkgimages=no`는 이 세션에 대한 객체 캐싱을 끌 때 사용할 수 있습니다. 이는 캐시 파일이 다시 생성되어야 함을 의미합니다. 기본적으로 Julia가 캐시하는 변형의 상한선에 대한 내용은 [`JULIA_MAX_NUM_PRECOMPILE_FILES`](@ref JULIA_MAX_NUM_PRECOMPILE_FILES)를 참조하십시오.

!!! note
    패키지 이미지가 네이티브 공유 라이브러리처럼 보이지만, 실제로는 그에 대한 근사치일 뿐입니다. 네이티브 프로그램에서 이들을 링크할 수 없으며, 반드시 Julia에서 로드해야 합니다.


## Linking

패키지 이미지에 네이티브 코드가 포함되어 있으므로 사용하기 전에 링커를 실행해야 합니다. 패키지 이미지 링킹 프로세스를 자세히 보려면 환경 변수 [`JULIA_VERBOSE_LINKING`](@ref JULIA_VERBOSE_LINKING)를 `true`로 설정할 수 있습니다.

또한, 사용자가 작동하는 시스템 링커를 설치했다고 가정할 수 없습니다. 따라서 Julia는 LLD, 즉 LLVM 링커를 함께 제공하여 즉시 사용할 수 있는 환경을 제공합니다. `base/linking.jl`에서는 모든 지원되는 플랫폼에서 패키지 이미지를 연결할 수 있는 제한된 인터페이스를 구현합니다.

### Quirks

LLD는 다중 플랫폼 링커임에도 불구하고 플랫폼 간 일관된 인터페이스를 제공하지 않습니다. 또한, `clang` 또는 다른 컴파일러 드라이버에서 사용하도록 설계되었기 때문에, 우리는 `llvm-project/clang/lib/Driver/ToolChains`의 일부 로직을 재구현합니다. 다행히도 `lld -flavor`를 사용하여 lld를 올바른 플랫폼으로 설정할 수 있습니다.

#### Windows

`link.exe`를 다루지 않기 위해 `-flavor gnu`를 사용하여 `lld`를 mingw32 환경의 크로스 링커로 전환합니다. Windows DLL은 `_DllMainCRTStartup` 함수를 포함해야 하며, mingw32 라이브러리에 대한 의존성을 최소화하기 위해 스텁 정의를 직접 주입합니다.

#### MacOS

macOS의 동적 라이브러리는 `-lSystem`에 링크해야 합니다. 최근 macOS 버전에서는 Xcode가 설치되어 있을 때만 `-lSystem`에 링크할 수 있습니다. 이를 위해 우리는 `-undefined dynamic_lookup`으로 링크합니다.

## [Package images optimized for multiple microarchitectures](@id pkgimgs-multi-versioning)

[multi-versioning](@ref sysimg-multi-versioning)와 유사하게, 패키지 이미지도 다중 버전을 지원합니다. 이질적인 환경에서 통합 캐시가 있는 경우, 환경 변수 `JULIA_CPU_TARGET=generic`을 설정하여 객체 캐시를 다중 버전으로 만들 수 있습니다.

## Flags that impact package image creation and selection

다음은 캐시 선택에 영향을 미치는 Julia 명령줄 플래그입니다. 서로 다른 플래그로 생성된 패키지 이미지는 거부됩니다.

  * `-g`, `--debug-info`: 코드 생성이 변경되므로 정확한 일치를 요구합니다.
  * `--check-bounds`: 정확한 일치를 요구합니다. 이는 코드 생성을 변경하기 때문입니다.
  * `--inline`: 정확한 일치가 필요합니다. 코드 생성이 변경되기 때문입니다.
  * `--pkgimages`: 객체 캐싱이 활성화되지 않은 상태에서 실행할 수 있도록 허용합니다.
  * `-O`, `--optimize`: 낮은 최적화 수준에 대해 생성된 패키지 이미지를 거부하지만, 더 높은 최적화 수준의 이미지는 로드할 수 있도록 허용합니다.
