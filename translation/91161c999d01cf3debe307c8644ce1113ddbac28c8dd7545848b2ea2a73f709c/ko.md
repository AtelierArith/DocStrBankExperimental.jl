# Environment Variables

Julia는 여러 환경 변수를 설정할 수 있으며, 이는 각 운영 체제에 대한 일반적인 방법으로 설정하거나 Julia 내에서 휴대 가능한 방법으로 설정할 수 있습니다. 환경 변수 [`JULIA_EDITOR`](@ref JULIA_EDITOR)를 `vim`으로 설정하고 싶다고 가정하면, `ENV["JULIA_EDITOR"] = "vim"`을 입력하여 (예를 들어, REPL에서) 이 변경을 사례별로 적용할 수 있으며, 사용자의 홈 디렉토리에 있는 사용자 구성 파일 `~/.julia/config/startup.jl`에 동일한 내용을 추가하여 영구적인 효과를 얻을 수 있습니다. 동일한 환경 변수의 현재 값은 `ENV["JULIA_EDITOR"]`를 평가하여 확인할 수 있습니다.

줄리아가 사용하는 환경 변수는 일반적으로 `JULIA`로 시작합니다. 만약 [`InteractiveUtils.versioninfo`](@ref)가 키워드 `verbose=true`로 호출되면, 출력은 줄리아와 관련된 정의된 환경 변수를 나열하며, 그 이름에 `JULIA`가 포함된 변수도 포함됩니다.

!!! note
    런타임 중에 환경 변수를 변경하는 것은 피하는 것이 좋습니다. 예를 들어 `~/.julia/config/startup.jl` 내에서 변경하는 것을 말합니다.

    한 가지 이유는 [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) 및 [`JULIA_PROJECT`](@ref JULIA_PROJECT)와 같은 일부 줄리아 언어 변수가 줄리아가 시작되기 전에 설정되어야 한다는 것입니다.

    유사하게, sysimage의 사용자 모듈의 `__init__()` 함수(패키지 컴파일러를 통해)는 `startup.jl` 이전에 실행되므로, `startup.jl`에서 환경 변수를 설정하는 것은 사용자 코드에 대해 너무 늦을 수 있습니다.

    또한, 런타임 중에 환경 변수를 변경하면 그렇지 않은 코드에 데이터 경합이 발생할 수 있습니다.

    Bash에서는 환경 변수를 수동으로 설정할 수 있습니다. 예를 들어, Julia를 시작하기 전에 `export JULIA_NUM_THREADS=4`를 실행하거나, `~/.bashrc` 또는 `~/.bash_profile`에 동일한 명령을 추가하여 Bash가 시작될 때마다 변수를 설정할 수 있습니다.


## File locations

### [`JULIA_BINDIR`](@id JULIA_BINDIR)

Julia 실행 파일이 포함된 디렉토리의 절대 경로로, 전역 변수 [`Sys.BINDIR`](@ref)를 설정합니다. `$JULIA_BINDIR`가 설정되지 않은 경우, Julia는 런타임에 `Sys.BINDIR` 값을 결정합니다.

실행 파일 자체는 다음 중 하나입니다.

```
$JULIA_BINDIR/julia
$JULIA_BINDIR/julia-debug
```

기본적으로.

전역 변수 `Base.DATAROOTDIR`는 `Sys.BINDIR`에서 줄리아와 관련된 데이터 디렉토리까지의 상대 경로를 결정합니다. 그런 다음 경로

```
$JULIA_BINDIR/$DATAROOTDIR/julia/base
```

소스 파일을 처음 검색하는 디렉토리를 결정합니다 ( `Base.find_source_file()`를 통해).

마찬가지로, 전역 변수 `Base.SYSCONFDIR`는 구성 파일 디렉토리에 대한 상대 경로를 결정합니다. 그런 다음 Julia는 `startup.jl` 파일을 다음 위치에서 검색합니다.

```
$JULIA_BINDIR/$SYSCONFDIR/julia/startup.jl
$JULIA_BINDIR/../etc/julia/startup.jl
```

기본적으로 (`Base.load_julia_startup()`를 통해).

예를 들어, `/bin/julia`에 위치한 Julia 실행 파일과 `../share`의 `DATAROOTDIR`, `../etc`의 `SYSCONFDIR`을 가진 Linux 설치는 `/bin`에 [`JULIA_BINDIR`](@ref JULIA_BINDIR)가 설정되고, 소스 파일 검색 경로는 다음과 같습니다.

```
/share/julia/base
```

및 전역 구성 검색 경로가

```
/etc/julia/startup.jl
```

### [`JULIA_PROJECT`](@id JULIA_PROJECT)

초기 활성 프로젝트가 되어야 하는 프로젝트를 나타내는 디렉토리 경로입니다. 이 환경 변수를 설정하는 것은 `--project` 시작 옵션을 지정하는 것과 동일한 효과가 있지만, `--project`가 더 높은 우선 순위를 가집니다. 변수가 `@.` (후행 점에 주의)로 설정되면, Julia는 현재 디렉토리와 그 상위 디렉토리에서 `Project.toml` 또는 `JuliaProject.toml` 파일이 포함된 프로젝트 디렉토리를 찾으려고 시도합니다. [Code Loading](@ref code-loading) 장도 참조하십시오.

!!! note
    [`JULIA_PROJECT`](@ref JULIA_PROJECT)는 julia를 시작하기 전에 정의되어야 합니다; `startup.jl`에서 정의하는 것은 시작 프로세스에서 너무 늦습니다.


### [`JULIA_LOAD_PATH`](@id JULIA_LOAD_PATH)

[`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) 환경 변수는 전역 Julia [`LOAD_PATH`](@ref) 변수를 채우는 데 사용되며, 이는 `import` 및 `using`을 통해 로드할 수 있는 패키지를 결정합니다(자세한 내용은 [Code Loading](@ref code-loading) 참조).

셸 `PATH` 변수와 달리, [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH)의 빈 항목은 `LOAD_PATH`를 채울 때 기본값인 `["@", "@v#.#", "@stdlib"]`로 확장됩니다. 이는 `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448`가 이미 설정되어 있는지 여부에 관계없이 셸 스크립트에서 로드 경로 값을 쉽게 추가하거나 앞에 붙일 수 있게 해줍니다. 예를 들어, 디렉토리 `/foo/bar`를 `LOAD_PATH`의 앞에 추가하려면 다음과 같이 하면 됩니다.

```sh
export JULIA_LOAD_PATH="/foo/bar:$JULIA_LOAD_PATH"
```

[`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) 환경 변수가 이미 설정되어 있다면, 이전 값은 `/foo/bar`로 앞에 추가됩니다. 반면에 `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448`가 설정되어 있지 않다면, `/foo/bar:`로 설정되며, 이는 `LOAD_PATH` 값이 `["/foo/bar", "@", "@v#.#", "@stdlib"]`로 확장됩니다. 만약 `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448`가 빈 문자열로 설정되어 있다면, 빈 `LOAD_PATH` 배열로 확장됩니다. 다시 말해, 빈 문자열은 빈 문자열의 하나의 요소 배열이 아니라, 제로 요소 배열로 해석됩니다. 이러한 동작은 환경 변수를 통해 빈 로드 경로를 설정할 수 있도록 선택되었습니다. 기본 로드 경로를 원한다면, 환경 변수를 해제하거나 값이 있어야 한다면 문자열 `:`로 설정하십시오.

!!! note
    Windows에서는 경로 요소가 `;` 문자로 구분되며, 이는 Windows의 대부분의 경로 목록에서도 마찬가지입니다.


### [`JULIA_DEPOT_PATH`](@id JULIA_DEPOT_PATH)

[`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) 환경 변수는 전역 Julia [`DEPOT_PATH`](@ref) 변수를 채우는 데 사용되며, 이는 패키지 관리자와 Julia의 코드 로딩 메커니즘이 패키지 레지스트리, 설치된 패키지, 명명된 환경, 리포지토리 클론, 캐시된 컴파일된 패키지 이미지, 구성 파일 및 REPL의 히스토리 파일의 기본 위치를 찾는 방법을 제어합니다.

셸 `PATH` 변수와는 달리 [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH)와 유사하게, [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH)의 빈 항목은 특별한 동작을 합니다:

  * 마지막에, 사용자 저장소를 *제외하고* `DEPOT_PATH`의 기본값으로 확장됩니다.
  * 시작할 때, 사용자 저장소를 *포함하여* `DEPOT_PATH`의 기본값으로 확장됩니다.

이것은 사용자 저장소를 쉽게 재정의할 수 있게 해주며, 여전히 캐시 파일, 아티팩트 등과 같이 Julia와 함께 번들된 리소스에 대한 접근을 유지합니다. 예를 들어, 사용자 저장소를 `/foo/bar`로 전환하려면 후행 `:`를 사용하세요.

```sh
export JULIA_DEPOT_PATH="/foo/bar:"
```

모든 패키지 작업, 예를 들어 레지스트리 복제나 패키지 설치는 이제 `/foo/bar`에 기록됩니다. 그러나 빈 항목이 기본 시스템 저장소로 확장되기 때문에 모든 번들 리소스는 여전히 사용 가능합니다. 만약 정말로 `/foo/bar`에 있는 저장소만 사용하고 번들 리소스를 로드하고 싶지 않다면, 환경 변수를 후행 콜론 없이 `/foo/bar`로 설정하면 됩니다.

기본 사용자 저장소를 포함한 전체 기본 목록의 끝에 저장소를 추가하려면 앞에 `:`를 사용하세요.

```sh
export JULIA_DEPOT_PATH=":/foo/bar"
```

위 규칙에는 두 가지 예외가 있습니다. 첫째, [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH)가 빈 문자열로 설정되면, 빈 `DEPOT_PATH` 배열로 확장됩니다. 다시 말해, 빈 문자열은 하나의 빈 문자열 배열이 아닌 제로 요소 배열로 해석됩니다. 이러한 동작은 환경 변수를 통해 빈 저장소 경로를 설정할 수 있도록 선택되었습니다.

둘째, [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH)에 사용자 저장소가 지정되지 않은 경우, 빈 항목은 기본 저장소로 확장됩니다 *사용자 저장소를 포함하여*. 이는 환경 변수가 설정되지 않은 것처럼 기본 저장소를 사용할 수 있게 하며, 이를 위해 문자열 `:`로 설정하면 됩니다.

!!! note
    Windows에서는 경로 요소가 `;` 문자로 구분되며, 이는 Windows의 대부분의 경로 목록에서도 마찬가지입니다.


!!! note
    [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) must be defined before starting julia; defining it in `startup.jl` is too late in the startup process; at that point you can instead directly modify the `DEPOT_PATH` array, which is populated from the environment variable.


### [`JULIA_HISTORY`](@id JULIA_HISTORY)

REPL의 히스토리 파일의 절대 경로 `REPL.find_hist_file()`입니다. `$JULIA_HISTORY`가 설정되어 있지 않으면 `REPL.find_hist_file()`는 기본값으로 설정됩니다.

```
$(DEPOT_PATH[1])/logs/repl_history.jl
```

### [`JULIA_MAX_NUM_PRECOMPILE_FILES`](@id JULIA_MAX_NUM_PRECOMPILE_FILES)

단일 패키지의 서로 다른 인스턴스가 사전 컴파일 캐시에 저장될 수 있는 최대 수를 설정합니다(기본값 = 10).

### [`JULIA_VERBOSE_LINKING`](@id JULIA_VERBOSE_LINKING)

true로 설정하면, 전처리 중에 링커 명령이 표시됩니다.

## Pkg.jl

### [`JULIA_CI`](@id JULIA_CI)

`true`로 설정하면, 이는 패키지 서버에 패키지 작업이 패키지 사용 통계 수집을 위한 지속적 통합(CI) 시스템의 일부임을 나타냅니다.

### [`JULIA_NUM_PRECOMPILE_TASKS`](@id JULIA_NUM_PRECOMPILE_TASKS)

패키지를 미리 컴파일할 때 사용할 병렬 작업의 수입니다. [`Pkg.precompile`](https://pkgdocs.julialang.org/v1/api/#Pkg.precompile).

### [`JULIA_PKG_DEVDIR`](@id JULIA_PKG_DEVDIR)

[`Pkg.develop`](https://pkgdocs.julialang.org/v1/api/#Pkg.develop)에서 패키지를 다운로드하는 데 사용되는 기본 디렉토리입니다.

### [`JULIA_PKG_IGNORE_HASHES`](@id JULIA_PKG_IGNORE_HASHES)

`1`로 설정하면 아티팩트의 잘못된 해시를 무시합니다. 이는 다운로드 검증을 비활성화하므로 주의해서 사용해야 하지만, 서로 다른 유형의 파일 시스템 간에 파일을 이동할 때 문제를 해결할 수 있습니다. 자세한 내용은 [Pkg.jl issue #2317](https://github.com/JuliaLang/Pkg.jl/issues/2317)를 참조하세요.

!!! compat "Julia 1.6"
    이것은 Julia 1.6 이상에서만 지원됩니다.


### [`JULIA_PKG_OFFLINE`](@id JULIA_PKG_OFFLINE)

`true`로 설정하면 오프라인 모드가 활성화됩니다: [`Pkg.offline`](https://pkgdocs.julialang.org/v1/api/#Pkg.offline).

!!! compat "Julia 1.5"
    Pkg의 오프라인 모드는 Julia 1.5 이상이 필요합니다.


### [`JULIA_PKG_PRECOMPILE_AUTO`](@id JULIA_PKG_PRECOMPILE_AUTO)

`0`으로 설정하면 매니페스트를 변경하는 패키지 작업에 의한 자동 사전 컴파일이 비활성화됩니다. [`Pkg.precompile`](https://pkgdocs.julialang.org/v1/api/#Pkg.precompile).

### [`JULIA_PKG_SERVER`](@id JULIA_PKG_SERVER)

패키지 레지스트리를 사용할 URL을 지정합니다. 기본적으로 `Pkg`는 Julia 패키지를 가져오기 위해 `https://pkg.julialang.org`를 사용합니다. 또한, PkgServer 프로토콜의 사용을 비활성화하고 대신 패키지를 호스트(GitHub, GitLab 등)에서 직접 액세스할 수 있도록 설정할 수 있습니다: `export JULIA_PKG_SERVER=""`

### [`JULIA_PKG_SERVER_REGISTRY_PREFERENCE`](@id JULIA_PKG_SERVER_REGISTRY_PREFERENCE)

선호하는 레지스트리 유형을 지정합니다. 현재 지원되는 값은 `conservative`(기본값)으로, 이는 저장 서버에 의해 처리된 리소스만 게시하며(따라서 PkgServers에서 사용할 수 있을 확률이 더 높습니다), 반면 `eager`는 저장 서버에 의해 반드시 처리되지 않은 리소스를 가진 레지스트리를 게시합니다. 임의의 서버에서 다운로드를 허용하지 않는 제한적인 방화벽 뒤에 있는 사용자는 `eager` 유형을 사용해서는 안 됩니다.

!!! compat "Julia 1.7"
    이것은 Julia 1.7 이상에만 영향을 미칩니다.


### [`JULIA_PKG_UNPACK_REGISTRY`](@id JULIA_PKG_UNPACK_REGISTRY)

`true`로 설정하면, 레지스트리를 압축된 tarball로 저장하는 대신 압축 해제합니다.

!!! compat "Julia 1.7"
    이것은 Julia 1.7 이상에만 영향을 미칩니다. 이전 버전은 항상 레지스트리를 압축 해제합니다.


### [`JULIA_PKG_USE_CLI_GIT`](@id JULIA_PKG_USE_CLI_GIT)

`true`로 설정하면, git 프로토콜을 사용하는 Pkg 작업은 기본 libgit2 라이브러리 대신 외부 `git` 실행 파일을 사용합니다.

!!! compat "Julia 1.7"
    `git` 실행 파일의 사용은 Julia 1.7 이상에서만 지원됩니다.


### [`JULIA_PKGRESOLVE_ACCURACY`](@id JULIA_PKGRESOLVE_ACCURACY)

패키지 해결자의 정확도. 이는 양의 정수여야 하며, 기본값은 `1`입니다.

### [`JULIA_PKG_PRESERVE_TIERED_INSTALLED`](@id JULIA_PKG_PRESERVE_TIERED_INSTALLED)

기본 패키지 설치 전략을 `Pkg.PRESERVE_TIERED_INSTALLED`로 변경하여 패키지 관리자가 이미 설치된 패키지의 버전을 최대한 유지하면서 패키지 버전을 설치하도록 하십시오.

!!! compat "Julia 1.9"
    이것은 Julia 1.9 이상에만 영향을 미칩니다.


## Network transport

### [`JULIA_NO_VERIFY_HOSTS`](@id JULIA_NO_VERIFY_HOSTS)

### [`JULIA_SSL_NO_VERIFY_HOSTS`](@id JULIA_SSL_NO_VERIFY_HOSTS)

### [`JULIA_SSH_NO_VERIFY_HOSTS`](@id JULIA_SSH_NO_VERIFY_HOSTS)

### [`JULIA_ALWAYS_VERIFY_HOSTS`](@id JULIA_ALWAYS_VERIFY_HOSTS)

호스트의 신원을 확인해야 하거나 확인하지 않아야 하는 특정 전송 계층을 지정합니다. [`NetworkOptions.verify_host`](https://github.com/JuliaLang/NetworkOptions.jl#verify_host)

### [`JULIA_SSL_CA_ROOTS_PATH`](@id JULIA_SSL_CA_ROOTS_PATH)

인증 기관 루트를 포함하는 파일 또는 디렉토리를 지정하십시오. [`NetworkOptions.ca_roots`](https://github.com/JuliaLang/NetworkOptions.jl#ca_roots)

## External applications

### [`JULIA_SHELL`](@id JULIA_SHELL)

Julia가 외부 명령을 실행하는 데 사용할 셸의 절대 경로( `Base.repl_cmd()`를 통해). 기본값은 환경 변수 `$SHELL`이며, `$SHELL`이 설정되지 않은 경우 `/bin/sh`로 대체됩니다.

!!! note
    Windows에서는 이 환경 변수가 무시되며, 외부 명령은 직접 실행됩니다.


### [`JULIA_EDITOR`](@id JULIA_EDITOR)

`InteractiveUtils.editor()`에 의해 반환된 편집기는 예를 들어 [`InteractiveUtils.edit`](@ref)에서 사용되며, 선호하는 편집기의 명령을 참조합니다. 예를 들어 `vim`입니다.

`$JULIA_EDITOR`는 `$VISUAL`보다 우선하며, `$VISUAL`는 다시 `$EDITOR`보다 우선합니다. 이 환경 변수들이 설정되어 있지 않으면, 편집기는 Windows와 OS X에서는 `open`으로, 존재하는 경우에는 `/etc/alternatives/editor`로, 그렇지 않으면 `emacs`로 간주됩니다.

Windows에서 Visual Studio Code를 사용하려면 `$JULIA_EDITOR`를 `code.cmd`로 설정하세요.

## Parallelization

### [`JULIA_CPU_THREADS`](@id JULIA_CPU_THREADS)

전역 변수 [`Base.Sys.CPU_THREADS`](@ref)를 재정의하여 사용 가능한 논리 CPU 코어 수를 설정합니다.

### [`JULIA_WORKER_TIMEOUT`](@id JULIA_WORKER_TIMEOUT)

[`Float64`](@ref)는 `Distributed.worker_timeout()`의 값을 설정합니다 (기본값: `60.0`). 이 함수는 작업 프로세스가 마스터 프로세스가 연결을 설정하기 위해 기다리는 초 수를 제공합니다.

### [`JULIA_NUM_THREADS`](@id JULIA_NUM_THREADS)

부호 없는 64비트 정수(`uint64_t`)로, Julia에서 사용할 수 있는 최대 스레드 수를 설정합니다. 만약 `$JULIA_NUM_THREADS`가 양수가 아니거나 설정되지 않았거나, 시스템 호출을 통해 CPU 스레드 수를 결정할 수 없는 경우, 스레드 수는 `1`로 설정됩니다.

`$JULIA_NUM_THREADS`가 `auto`로 설정되면, 스레드 수는 CPU 스레드 수로 설정됩니다.

!!! note
    `JULIA_NUM_THREADS`는 julia를 시작하기 전에 정의되어야 합니다; `startup.jl`에서 정의하는 것은 시작 과정에서 너무 늦습니다.


!!! compat "Julia 1.5"
    Julia 1.5 이상에서는 `-t`/`--threads` 명령줄 인수를 사용하여 시작 시 스레드 수를 지정할 수 있습니다.


!!! compat "Julia 1.7"
    `$JULIA_NUM_THREADS`의 `auto` 값은 Julia 1.7 이상이 필요합니다.


### [`JULIA_THREAD_SLEEP_THRESHOLD`](@id JULIA_THREAD_SLEEP_THRESHOLD)

문자열이 대소문자를 구분하지 않는 하위 문자열 `"infinite"`로 시작하도록 설정되면, 스피닝 스레드는 절대 잠들지 않습니다. 그렇지 않으면, `$JULIA_THREAD_SLEEP_THRESHOLD`는 부호 없는 64비트 정수(`uint64_t`)로 해석되며, 스피닝 스레드가 잠들기 전의 시간(나노초 단위)을 제공합니다.

### [`JULIA_NUM_GC_THREADS`](@id JULIA_NUM_GC_THREADS)

가비지 수집에 사용되는 스레드 수를 설정합니다. 지정하지 않으면 작업자 스레드 수의 절반으로 설정됩니다.

!!! compat "Julia 1.10"
    환경 변수는 1.10에 추가되었습니다.


### [`JULIA_IMAGE_THREADS`](@id JULIA_IMAGE_THREADS)

이 Julia 프로세스에서 이미지 컴파일에 사용되는 스레드 수를 설정하는 부호 없는 32비트 정수입니다. 이 변수의 값은 모듈이 작은 모듈인 경우 무시될 수 있습니다. 지정하지 않으면 [`JULIA_CPU_THREADS`](@ref JULIA_CPU_THREADS)의 값 또는 논리 CPU 코어 수의 절반 중 더 작은 값이 대신 사용됩니다.

### [`JULIA_IMAGE_TIMINGS`](@id JULIA_IMAGE_TIMINGS)

이미지 컴파일 중에 자세한 타이밍 정보가 출력되는지 여부를 결정하는 불리언 값입니다. 기본값은 0입니다.

### [`JULIA_EXCLUSIVE`](@id JULIA_EXCLUSIVE)

`0`가 아닌 값으로 설정되면 Julia의 스레드 정책은 전용 머신에서 실행되는 것과 일치합니다: 마스터 스레드는 프로세서 0에 있으며, 스레드는 고정되어 있습니다. 그렇지 않으면 Julia는 운영 체제가 스레드 정책을 처리하도록 허용합니다.

## REPL formatting

REPL 출력이 터미널에서 어떻게 형식화되어야 하는지를 결정하는 환경 변수입니다. 일반적으로 이러한 변수는 [ANSI terminal escape sequences](https://en.wikipedia.org/wiki/ANSI_escape_code)로 설정되어야 합니다. Julia는 많은 동일한 기능을 갖춘 고급 인터페이스를 제공합니다. [The Julia REPL](@ref) 섹션을 참조하십시오.

### [`JULIA_ERROR_COLOR`](@id JULIA_ERROR_COLOR)

형식 `Base.error_color()` (기본값: 연한 빨강, `"\033[91m"`)은 터미널에서 오류가 가져야 하는 색상입니다.

### [`JULIA_WARN_COLOR`](@id JULIA_WARN_COLOR)

경고는 터미널에서 `Base.warn_color()` (기본값: 노란색, `"\033[93m"`) 형식을 가져야 합니다.

### [`JULIA_INFO_COLOR`](@id JULIA_INFO_COLOR)

`Base.info_color()` (기본값: 청록색, `"\033[36m"`)은 터미널에서 정보가 가져야 할 형식입니다.

### [`JULIA_INPUT_COLOR`](@id JULIA_INPUT_COLOR)

`Base.input_color()` (기본값: normal, `"\033[0m"`) 터미널에서 입력이 가져야 하는 형식입니다.

### [`JULIA_ANSWER_COLOR`](@id JULIA_ANSWER_COLOR)

`Base.answer_color()` (기본값: normal, `"\033[0m"`) 출력은 터미널에서 가져야 합니다.

## System and Package Image Building

### [`JULIA_CPU_TARGET`](@id JULIA_CPU_TARGET)

대상 머신 아키텍처를 수정하여 [system](@ref sysimg-multi-versioning) 및 [package images](@ref pkgimgs-multi-versioning)를 (사전)컴파일합니다. `JULIA_CPU_TARGET`는 디스크 캐시에 출력되는 머신 코드 이미지 생성에만 영향을 미칩니다. `--cpu-target` 또는 `-C`와 달리, [command line option](@ref cli)는 Julia 세션 내에서 JIT(즉시 컴파일) 코드 생성에 영향을 미치지 않으며, 이 경우 머신 코드는 메모리에만 저장됩니다.

[`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET)의 유효한 값은 `julia -C help`를 실행하여 얻을 수 있습니다.

[`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) 설정은 서로 다른 유형이나 기능의 프로세서가 존재할 수 있는 이질적 컴퓨팅 시스템에서 중요합니다. 이는 구성 요소 노드가 서로 다른 프로세서를 사용할 수 있는 고성능 컴퓨팅(HPC) 클러스터에서 일반적으로 발생합니다.

CPU 타겟 문자열은 `;`로 구분된 문자열 목록이며, 각 문자열은 CPU 또는 아키텍처 이름으로 시작하고 선택적으로 `,`로 구분된 기능 목록이 뒤따릅니다. `generic` 또는 빈 CPU 이름은 C/C++ 런타임이 컴파일된 아키텍처 이상인 타겟 ISA의 기본 필수 기능 세트를 의미합니다. 각 문자열은 LLVM에 의해 해석됩니다.

몇 가지 특별한 기능이 지원됩니다:

1. `clone_all`

    이것은 대상을 sysimg의 모든 함수를 복제하도록 강제합니다. 부정형으로 사용될 때(즉, `-clone_all`), 이는 특정 대상에 대해 기본적으로 활성화된 전체 복제를 비활성화합니다.
2. `base([0-9]*)`

    이것은 (0부터 시작하는) 기본 대상 인덱스를 지정합니다. 기본 대상은 현재 대상이 기반하고 있는 대상이며, 즉 복제되지 않는 함수는 기본 대상의 버전을 사용합니다. 이 옵션은 기본 대상이 기본 대상(0)이 아닐 경우 완전히 복제되도록 합니다(마치 `clone_all`이 지정된 것처럼). 인덱스는 현재 인덱스보다 작을 수만 있습니다.
3. `opt_size`

    크기 최적화 및 최소 성능 영향을 위해. Clang/GCC의 `-Os`.
4. `최소_크기`

    크기만 최적화합니다. Clang의 `-Oz`.

## Debugging and profiling

### [`JULIA_DEBUG`](@id JULIA_DEBUG)

파일이나 모듈에 대한 디버그 로깅을 활성화하려면 [`Logging`](@ref man-logging)를 참조하세요.

### [`JULIA_PROFILE_PEEK_HEAP_SNAPSHOT`](@id JULIA_PROFILE_PEEK_HEAP_SNAPSHOT)

실행 중 프로파일링 피크 메커니즘을 통해 힙 스냅샷 수집을 활성화합니다. [Triggered During Execution](@ref)를 참조하세요.

### [`JULIA_TIMING_SUBSYSTEMS`](@id JULIA_TIMING_SUBSYSTEMS)

특정 Julia 실행을 위해 영역을 활성화하거나 비활성화할 수 있습니다. 예를 들어, 변수를 `+GC,-INFERENCE`로 설정하면 `GC` 영역이 활성화되고 `INFERENCE` 영역이 비활성화됩니다. [Dynamically Enabling and Disabling Zones](@ref)를 참조하세요.

### [`JULIA_GC_ALLOC_POOL`](@id JULIA_GC_ALLOC_POOL)

### [`JULIA_GC_ALLOC_OTHER`](@id JULIA_GC_ALLOC_OTHER)

### [`JULIA_GC_ALLOC_PRINT`](@id JULIA_GC_ALLOC_PRINT)

설정된 경우, 이러한 환경 변수는 선택적으로 문자 `'r'`로 시작하는 문자열을 사용하며, 뒤이어 세 개의 부호 있는 64비트 정수(`int64_t`)로 콜론으로 구분된 리스트의 문자열 보간이 옵니다. 이 세 개의 정수 `a:b:c`는 산술 수열 `a`, `a + b`, `a + 2*b`, ... `c`를 나타냅니다.

  * `jl_gc_pool_alloc()`가 `n`번째 호출된 경우, `n`이 `$JULIA_GC_ALLOC_POOL`로 표현되는 산술 수열에 속하면 가비지 컬렉션이 강제로 수행됩니다.
  * `maybe_collect()`가 호출된 `n`번째 경우이고, `n`이 `$JULIA_GC_ALLOC_OTHER`로 표현되는 산술 수열에 속한다면, 가비지 수집이 강제로 수행됩니다.
  * `jl_gc_collect()`가 호출된 `n`번째 경우이고, `n`이 `$JULIA_GC_ALLOC_PRINT`로 표현되는 산술 수열에 속한다면, `jl_gc_pool_alloc()` 및 `maybe_collect()`에 대한 호출 수가 출력됩니다.

환경 변수의 값이 문자 `'r'`로 시작하면 가비지 수집 이벤트 간의 간격이 무작위화됩니다.

!!! note
    이 환경 변수는 Julia가 가비지 컬렉션 디버깅으로 컴파일된 경우에만 효과가 있습니다(즉, 빌드 구성에서 `WITH_GC_DEBUG_ENV`가 `1`로 설정된 경우).


### [`JULIA_GC_NO_GENERATIONAL`](@id JULIA_GC_NO_GENERATIONAL)

`0`이 아닌 값으로 설정하면, Julia 가비지 컬렉터는 메모리에 대한 "빠른 스윕"을 수행하지 않습니다.

!!! note
    이 환경 변수는 Julia가 가비지 컬렉션 디버깅으로 컴파일된 경우에만 효과가 있습니다(즉, 빌드 구성에서 `WITH_GC_DEBUG_ENV`가 `1`로 설정된 경우).


### [`JULIA_GC_WAIT_FOR_DEBUGGER`](@id JULIA_GC_WAIT_FOR_DEBUGGER)

`0`이 아닌 값으로 설정하면, Julia 가비지 컬렉터는 치명적인 오류가 발생할 때 중단하는 대신 디버거가 연결될 때까지 기다립니다.

!!! note
    이 환경 변수는 Julia가 가비지 컬렉션 디버깅으로 컴파일된 경우에만 효과가 있습니다(즉, 빌드 구성에서 `WITH_GC_DEBUG_ENV`가 `1`로 설정된 경우).


### [`ENABLE_JITPROFILING`](@id ENABLE_JITPROFILING)

`0`이 아닌 값으로 설정하면, 컴파일러는 즉시 프로파일링(JIT 프로파일링)을 위한 이벤트 리스너를 생성하고 등록합니다.

!!! note
    이 환경 변수는 Julia가 JIT 프로파일링 지원으로 컴파일된 경우에만 효과가 있습니다.

      * 인텔의 [VTune™ Amplifier](https://software.intel.com/en-us/vtune) (`USE_INTEL_JITEVENTS`가 빌드 구성에서 `1`로 설정됨), 또는
      * [OProfile](https://oprofile.sourceforge.io/news/) (`USE_OPROFILE_JITEVENTS`가 빌드 구성에서 `1`로 설정됨).
      * [Perf](https://perf.wiki.kernel.org) (`USE_PERF_JITEVENTS`가 빌드 구성에서 `1`로 설정됨). 이 통합은 기본적으로 활성화되어 있습니다.


### [`ENABLE_GDBLISTENER`](@id ENABLE_GDBLISTENER)

`0` 이외의 값으로 설정하면 릴리스 빌드에서 Julia 코드의 GDB 등록이 활성화됩니다. Julia의 디버그 빌드에서는 항상 활성화됩니다. `-g 2`와 함께 사용하는 것이 권장됩니다.

### [`JULIA_LLVM_ARGS`](@id JULIA_LLVM_ARGS)

LLVM 백엔드에 전달될 인수.

### `JULIA_FALLBACK_REPL`

REPL.jl 대신 폴백 REPL을 강제로 사용합니다.
