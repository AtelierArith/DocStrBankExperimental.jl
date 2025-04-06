# Binary distributions

이 노트는 다양한 플랫폼에서 배포하기 위해 Julia의 바이너리 배포판을 컴파일하려는 사람들을 위한 것입니다. 우리는 사용자가 가능한 한 넓은 범위의 운영 체제와 하드웨어 구성에서 Julia를 시도하고 널리 퍼뜨리는 것을 좋아합니다. 각 플랫폼마다 휴대 가능하고 작동하는 Julia 배포판을 만들기 위해 따라야 할 특정 문제와 프로세스가 있으므로 대부분의 노트를 OS별로 구분했습니다.

다음과 같이 주의하세요. Julia의 코드는 [MIT-licensed, with a few exceptions](https://github.com/JuliaLang/julia/blob/master/LICENSE.md)입니다. 그러나 여기서 설명된 기술로 생성된 배포판은 GPL 라이센스가 적용됩니다. `SuiteSparse`와 같은 다양한 의존 라이브러리가 GPL 라이센스이기 때문입니다. 우리는 미래에 비-GPL 배포판의 Julia를 제공할 수 있기를 희망합니다.

## Versioning and Git

Makefile은 `VERSION` 파일과 git 저장소의 커밋 해시 및 태그를 사용하여 스플래시 화면과 `versioninfo()` 출력에 채우는 데 사용하는 정보를 포함한 `base/version_git.jl`을 생성합니다. 어떤 이유로든 빌드할 때 git 저장소를 사용할 수 없으려면 다음 명령어로 `base/version_git.jl` 파일을 미리 생성해야 합니다:

```
make -C base version_git.jl.phony
```

줄리아는 인기 있는 패키지 관리자에 아직 포함되지 않은 패치된 버전을 사용하는 많은 빌드 종속성을 가지고 있습니다. 이러한 종속성은 일반적으로 빌드할 때 자동으로 다운로드되지만, 인터넷에 접속할 수 없는 컴퓨터에서 줄리아를 빌드할 수 있도록 하려면 특별한 make 타겟을 사용하여 전체 소스 배포 아카이브를 생성해야 합니다.

```
make full-source-dist
```

필요한 모든 종속성이 포함된 julia-version-commit.tar.gz 아카이브를 생성합니다.

태그가 있는 릴리스를 git 저장소에서 컴파일할 때, 스플래시 화면에 브랜치/커밋 해시 정보를 표시하지 않습니다. 최대 45자까지의 릴리스 설명을 표시하려면 이 줄을 사용할 수 있습니다. 이 줄을 설정하려면 Make.user 파일을 생성해야 합니다:

```
override TAGGED_RELEASE_BANNER = "my-package-repository build"
```

## Target Architectures

기본적으로 Julia는 시스템 이미지를 빌드 머신의 네이티브 아키텍처에 맞게 최적화합니다. 이는 패키지를 빌드할 때 일반적으로 원하는 것이 아니며, 호환되지 않는 CPU(특히 더 제한된 명령어 집합을 가진 구형 CPU)가 있는 어떤 머신에서든 Julia가 시작할 때 실패하게 만듭니다.

따라서 `make`를 호출할 때 `MARCH` 변수를 전달하여 지원하려는 기준 대상을 설정할 것을 권장합니다. 이는 Julia 실행 파일과 라이브러리, 그리고 시스템 이미지의 대상 CPU를 결정합니다(후자는 [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET)를 사용하여 설정할 수도 있습니다). x86 CPU에 일반적으로 유용한 값은 `x86-64` 및 `core2`(64비트 빌드를 위한)와 `pentium4`(32비트 빌드를 위한)입니다. 불행히도 Pentium 4보다 오래된 CPU는 현재 지원되지 않습니다(자세한 내용은 [this issue](https://github.com/JuliaLang/julia/issues/7185)를 참조하십시오).

LLVM이 지원하는 CPU 타겟의 전체 목록은 `llc -mattr=help`를 실행하여 얻을 수 있습니다.

## Linux

리눅스에서 `make binary-dist`는 완전한 기능을 갖춘 줄리아 설치가 포함된 tarball을 생성합니다. `.deb` 또는 `.rpm`과 같은 배포 패키지를 생성하려면 추가적인 노력이 필요합니다. Debian 및 Ubuntu 기반 시스템을 위한 `.deb` 패키지를 생성하는 데 필요한 메타데이터의 예는 [julia-debian](https://github.com/staticfloat/julia-debian) 리포지토리를 참조하십시오. RPM 기반 배포판에 대해서는 [Fedora package](https://src.fedoraproject.org/rpms/julia)를 참조하십시오. 아직 실험해 보지는 않았지만, [Alien](https://wiki.debian.org/Alien)는 다양한 리눅스 배포판을 위한 줄리아 패키지를 생성하는 데 사용될 수 있습니다.

Julia는 `make` 및 `make install`을 호출할 때 전달할 수 있는 `prefix` 및 기타 환경 변수를 통해 표준 설치 디렉토리를 재정의하는 것을 지원합니다. 그 목록은 Make.inc를 참조하세요. `DESTDIR`을 사용하여 임시 디렉토리에 설치를 강제할 수도 있습니다.

기본적으로 Julia는 `$prefix/etc/julia/startup.jl`을 설치 전역 초기화 파일로 로드합니다. 이 파일은 배포 관리자들이 사용자 정의 경로 또는 초기화 코드를 설정하는 데 사용할 수 있습니다. Linux 배포 패키지의 경우, `$prefix`가 `/usr`로 설정되어 있으면 `/usr/etc`를 찾을 수 없습니다. 이는 Julia의 개인 `etc` 디렉토리에 대한 경로를 변경해야 함을 의미합니다. 이는 빌드할 때 `sysconfdir` 메이크 변수를 통해 수행할 수 있습니다. 빌드할 때 `make`에 `sysconfdir=/etc`를 전달하면 Julia는 먼저 `/etc/julia/startup.jl`을 확인한 후 `$prefix/etc/julia/startup.jl`을 시도합니다.

## OS X

OSX에서 이진 배포를 만들려면 먼저 Julia를 빌드한 다음 `contrib/mac/app`로 이동하고, Julia를 빌드할 때 사용한 것과 동일한 makevars로 `make`를 실행합니다. 그러면 `contrib/mac/app` 디렉토리에 완전히 독립적인 Julia.app을 포함하는 `.dmg` 파일이 생성됩니다.

대안으로, Julia는 `make`를 `darwinframework` 타겟과 `DARWIN_FRAMEWORK=1`을 설정하여 호출함으로써 프레임워크로 빌드될 수 있습니다. 예를 들어, `make DARWIN_FRAMEWORK=1 darwinframework`.

## Windows

윈도우에서 Julia 배포판을 만드는 방법에 대한 지침은 [build devdocs for Windows](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/windows.md)에 설명되어 있습니다.

## Notes on BLAS and LAPACK

줄리아는 기본적으로 BLAS 및 LAPACK 라이브러리를 포함하는 OpenBLAS를 빌드합니다. 32비트 아키텍처에서는 줄리아가 32비트 정수를 사용하도록 OpenBLAS를 빌드하고, 64비트 아키텍처에서는 64비트 정수(ILP64)를 사용하도록 OpenBLAS를 빌드합니다. BLAS 및 LAPACK API 루틴을 호출하는 모든 줄리아 함수가 올바른 너비의 정수를 사용해야 합니다.

대부분의 BLAS 및 LAPACK 배포판은 리눅스 배포판에서 제공되며, 상용 구현조차도 32비트 API를 사용하는 라이브러리를 제공합니다. 많은 경우, 64비트 API는 별도의 라이브러리로 제공됩니다.

벤더 제공 또는 OS 제공 라이브러리를 사용할 때, Julia 빌드의 일환으로 `USE_BLAS64`라는 `make` 옵션이 제공됩니다. `make USE_BLAS64=0`을 실행하면, Julia는 64비트 아키텍처에서도 모든 정수가 32비트 너비인 32비트 API를 가정하여 BLAS와 LAPACK를 호출합니다.

줄리아가 사용하는 다른 라이브러리, 예를 들어 SuiteSparse도 내부적으로 BLAS와 LAPACK를 사용합니다. API는 BLAS와 LAPACK에 의존하는 모든 라이브러리에서 일관성을 유지해야 합니다. 줄리아 빌드 프로세스는 이러한 모든 라이브러리를 올바르게 빌드하지만, 기본값을 재정의하고 시스템에서 제공하는 라이브러리를 사용할 때는 이 일관성을 보장해야 합니다.

또한 Linux 배포판은 때때로 여러 버전의 OpenBLAS를 제공하는데, 그 중 일부는 멀티스레딩을 지원하고 다른 일부는 직렬 방식으로만 작동합니다. 예를 들어, Fedora에서는 `libopenblasp.so`가 스레드 방식이지만 `libopenblas.so`는 그렇지 않습니다. 최적의 성능을 위해 전자를 사용하는 것을 권장합니다. 기본 `libopenblas.so`와 이름이 다른 OpenBLAS 라이브러리를 선택하려면 `make`에 `LIBBLAS=-l$(YOURBLAS)` 및 `LIBBLASNAME=lib$(YOURBLAS)`를 전달하고, `$(YOURBLAS)`를 라이브러리 이름으로 바꾸십시오. 패키지가 버전이 없는 `.so` 심볼릭 링크 없이 작동하도록 하려면 라이브러리 이름에 `.so.0`을 추가할 수도 있습니다.

마지막으로, OpenBLAS는 자체 최적화된 LAPACK 버전을 포함합니다. `USE_SYSTEM_BLAS=1` 및 `USE_SYSTEM_LAPACK=1`로 설정하면 `LIBLAPACK=-l$(YOURBLAS)` 및 `LIBLAPACKNAME=lib$(YOURBLAS)`도 설정해야 합니다. 그렇지 않으면 참조 LAPACK가 사용되며 성능이 일반적으로 훨씬 낮습니다.

Julia 1.7부터 Julia는 [libblastrampoline](https://github.com/JuliaLinearAlgebra/libblastrampoline)를 사용하여 런타임에 다른 BLAS를 선택합니다.

# Point releasing 101

점/패치 릴리스를 만드는 것은 여러 가지 구별된 단계로 구성됩니다.

## Backporting commits

일부 풀 리퀘스트는 "backport pending x.y"로 레이블이 지정됩니다. 예를 들어, "backport pending 0.6". 이는 release-x.y 브랜치에서 태그가 지정된 다음 릴리스에 해당 풀 리퀘스트의 커밋이 포함되어야 함을 나타냅니다. 풀 리퀘스트가 마스터에 병합되면 각 커밋은 [cherry picked](https://git-scm.com/docs/git-cherry-pick) 전용 브랜치로 이동되어 궁극적으로 release-x.y에 병합됩니다.

### Creating a backports branch

먼저, release-x.y를 기반으로 새 브랜치를 만듭니다. Julia 브랜치의 일반적인 규칙은 개인 브랜치인 경우 브랜치 이름 앞에 자신의 이니셜을 붙이는 것입니다. 예를 들어, 브랜치의 작성자가 Jane Smith라고 가정해 보겠습니다.

```
git fetch origin
git checkout release-x.y
git rebase origin/release-x.y
git checkout -b js/backport-x.y
```

이것은 새로운 브랜치를 생성하기 전에 로컬의 release-x.y 복사본이 origin과 최신 상태인지 확인합니다.

### Cherry picking commits

이제 실제 백포팅을 진행합니다. GitHub 웹 UI에서 "backport pending x.y" 레이블이 붙은 모든 병합된 풀 리퀘스트를 찾습니다. 각 풀 리퀘스트의 하단으로 스크롤하여 "someperson merged commit `123abc` into `master` XX minutes ago"라고 표시된 부분을 확인합니다. 커밋 이름은 링크입니다. 클릭하면 커밋의 내용을 볼 수 있습니다. 이 페이지에서 `123abc`가 병합 커밋으로 표시되면 PR 페이지로 돌아가야 합니다. 우리는 병합 커밋을 원하지 않으며, 실제 커밋을 원합니다. 그러나 병합 커밋이 표시되지 않으면 PR이 스쿼시 병합되었다는 의미입니다. 이 경우, 이 페이지에 나열된 커밋 옆의 git SHA를 사용합니다.

커밋의 SHA를 얻은 후, 이를 백포팅 브랜치에 체리픽합니다:

```
git cherry-pick -x -e <sha>
```

수동으로 해결해야 할 충돌이 있을 수 있습니다. 충돌이 해결되면(해당되는 경우) 커밋 메시지 본문에 커밋을 도입한 GitHub 풀 리퀘스트에 대한 참조를 추가하세요.

모든 관련 커밋이 백포트 브랜치에 있으면, 브랜치를 GitHub에 푸시합니다.

## Checking for performance regressions

포인트 릴리스는 성능 저하를 절대 도입해서는 안 됩니다. 다행히도 Julia 벤치마킹 봇인 Nanosoldier는 마스터 브랜치뿐만 아니라 모든 브랜치에 대해 벤치마크를 실행할 수 있습니다. 이 경우 js/backport-x.y의 벤치마크 결과를 release-x.y와 비교하고자 합니다. 이를 위해 백포팅 풀 리퀘스트에 댓글을 달아 Nanosoldier를 로봇 잠에서 깨워주세요:

```markdown
@nanosoldier `runbenchmarks(ALL, vs=":release-x.y")`
```

이것은 release-x.y 및 js/backport-x.y에서 모든 등록된 벤치마크를 실행하고 결과 요약을 생성하여 모든 개선 사항과 퇴보를 표시합니다.

Nanosoldier가 어떤 회귀를 발견하면, 로컬에서 검증을 시도하고 필요하다면 Nanosoldier를 다시 실행하세요. 회귀가 단순한 잡음이 아닌 실제 문제로 판단되면, 이를 수정하는 마스터의 커밋을 찾아서 백포트해야 합니다. 만약 그런 커밋이 없다면, 회귀의 원인을 파악하고 패치를 제출해야 합니다(또는 코드를 아는 사람에게 패치를 제출하도록 요청하세요). 그런 다음, 패치가 병합되면 커밋을 백포트하세요. (적절하다면 백포트 브랜치에 직접 패치를 제출할 수도 있습니다.)

## Building test binaries

백포트 PR이 `release-x.y` 브랜치에 병합된 후, 로컬 클론의 Julia를 업데이트하고 다음을 사용하여 브랜치의 SHA를 가져옵니다.

```
git rev-parse origin/release-x.y
```

그것을 손에 두세요. 빌드봇 UI의 "Revision" 필드에 입력할 내용입니다.

현재로서는 PackageEvaluator를 실행하는 데 사용되는 Linux x86-64용 바이너리만 필요합니다. https://buildog.julialang.org로 이동하여 `nuke_linux64`에 대한 작업을 제출한 다음, SHA를 수정으로 제공하여 `package_linux64`에 대한 작업을 대기열에 추가합니다. 패키징 작업이 완료되면 바이너리가 AWS의 `julialang2` 버킷에 업로드됩니다. URL을 가져오세요. 이 URL은 PackageEvaluator에 사용됩니다.

## Checking for package breakages

포인트 릴리스는 결코 패키지를 깨뜨려서는 안 되며, 사용자에게 노출될 의도가 아닌 Base 내부를 사용하여 심각하게 의심스러운 해킹을 하는 패키지의 경우에만 예외가 될 수 있습니다. (그런 경우에는 패키지 저자와 이야기를 나눠보는 것이 좋습니다.)

앞으로 출시될 새로운 버전에서 변경 사항이 패키지를 깨뜨릴지 확인하는 것은 [PackageEvaluator](https://github.com/JuliaCI/PackageEvaluator.jl)를 사용하여 수행할 수 있으며, 일반적으로 "PkgEval"이라고 줄여 부릅니다. PkgEval은 GitHub 리포지토리와 pkg.julialang.org의 상태 배지를 채우는 역할을 합니다. 일반적으로 Nanosoldier의 비벤치마크 노드 중 하나에서 실행되며, Vagrant를 사용하여 별도의 병렬 VirtualBox 가상 머신에서 작업을 수행합니다.

### Setting up PackageEvaluator

패키지 평가기를 복제하고 `backport-x.y.z`라는 브랜치를 생성한 후 체크아웃하세요. 필요한 변경 사항은 약간 해킹적이고 혼란스러우며, 이는 향후 패키지 평가기 버전에서 해결될 것으로 기대됩니다. 변경 사항은 [this commit](https://github.com/JuliaCI/PackageEvaluator.jl/commit/5ba6a3b000e7a3793391d16f695c8704b91d6016)를 모델로 삼아야 합니다.

설정 스크립트는 첫 번째 인수로 실행할 Julia의 버전을, 두 번째 인수로 패키지 이름의 범위를 받습니다 (A-K의 경우 AK, L-Z의 경우 LZ). 기본 아이디어는 현재 x.y 릴리스와 우리의 백포트 버전, 각각 세 가지 패키지 범위로만 두 개의 Julia 버전을 실행하도록 약간 조정하는 것입니다.

연결된 차이에서 우리는 두 번째 인수가 LZ인 경우, 우리의 백포트 브랜치에서 빌드된 바이너리를 사용하고, 그렇지 않으면 (AK) 릴리스 바이너리를 사용한다고 말하고 있습니다. 그런 다음 첫 번째 인수를 사용하여 패키지 목록의 섹션을 실행합니다: 입력 0.4에 대해 A-F, 0.5에 대해 G-N, 0.6에 대해 O-Z입니다.

### Running PackageEvaluator

PkgEval을 실행하려면 충분히 강력한 머신(예: Nanosoldier 노드 1)을 찾은 다음 실행하세요.

```
git clone https://github.com/JuliaCI/PackageEvaluator.jl.git
cd PackageEvaluator.jl/scripts
git checkout backport-x.y.z
./runvagrant.sh
```

이것은 scripts/ 디렉토리에 몇 개의 폴더를 생성합니다. 폴더 이름과 그 내용은 아래에 디코딩되어 있습니다:

| Folder name | Julia version | Package range |
|:-----------:|:-------------:|:-------------:|
|    0.4AK    |    Release    |      A-F      |
|    0.4LZ    |   Backport    |      A-F      |
|    0.5AK    |    Release    |      G-N      |
|    0.5LZ    |   Backport    |      G-N      |
|    0.6AK    |    Release    |      O-Z      |
|    0.6LZ    |   Backport    |      O-Z      |

### Investigating results

작업이 완료되면, 동일한 디렉토리에서 `./summary.sh`를 사용하여 발견된 내용을 요약한 보고서를 생성할 수 있습니다. 각 폴더에 대해 이를 수행하여 버전별로 전체 결과를 집계할 것입니다.

```
./summary.sh 0.4AK/*.json > summary_release.txt
./summary.sh 0.5AK/*.json >> summary_release.txt
./summary.sh 0.6AK/*.json >> summary_release.txt
./summary.sh 0.4LZ/*.json > summary_backport.txt
./summary.sh 0.5LZ/*.json >> summary_backport.txt
./summary.sh 0.6LZ/*.json >> summary_backport.txt
```

이제 두 개의 파일, `summary_release.txt`와 `summary_backport.txt`가 있으며, 두 버전의 각 패키지에 대한 PackageEvaluator 테스트 결과(통과/실패)가 포함되어 있습니다.

이것들을 Julia에 더 쉽게 가져오기 위해, CSV 파일로 변환한 다음 DataFrames 패키지를 사용하여 결과를 처리하겠습니다. CSV로 변환하려면 각 .txt 파일을 해당 .csv 파일로 복사한 다음 Vim에 들어가서 `ggVGI"<esc>`를 실행한 후 `:%s/\.json /",/g`를 입력합니다. (Vim을 사용할 필요는 없습니다; 이것은 단지 한 가지 방법일 뿐입니다.) 이제 다음과 유사한 Julia 코드를 사용하여 결과를 처리합니다.

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

이것은 `stdout`에 색상 코드가 있는 줄을 작성합니다. 빨간색으로 표시된 모든 줄은 백포트 버전으로 인해 발생할 수 있는 문제를 나타내므로 조사해야 합니다. 노란색 줄은 어떤 이유로 한 버전에서는 패키지가 실행되었지만 다른 버전에서는 실행되지 않았음을 의미하므로 살펴봐야 합니다. 백포트된 브랜치가 문제를 일으키고 있다고 판단되면, `git bisect`를 사용하여 문제의 커밋을 식별하고, 해당 커밋을 `git revert`한 후 이 과정을 반복하세요.

## Merging backports into the release branch

확인한 후에

  * 백포트된 커밋은 모든 줄리아의 단위 테스트를 통과합니다.
  * 백포트된 커밋으로 인해 릴리스 브랜치와 비교했을 때 성능 저하가 발생하지 않습니다, 그리고
  * 백포트된 커밋은 등록된 패키지를 깨뜨리지 않습니다.

그런 다음 백포트 브랜치가 release-x.y에 병합될 준비가 되었습니다. 병합이 완료되면 백포트된 커밋을 포함하는 모든 풀 리퀘스트에서 "backport pending x.y" 레이블을 제거하십시오. 백포트되지 않은 PR에서는 레이블을 제거하지 마십시오.

release-x.y 브랜치에는 이제 모든 새로운 커밋이 포함되어야 합니다. 브랜치에서 마지막으로 하고 싶은 것은 버전 번호를 조정하는 것입니다. 이를 위해 VERSION 파일을 편집하여 버전 번호에서 `-pre`를 제거하는 PR을 release-x.y에 제출하세요. 머지가 완료되면 태그를 달 준비가 된 것입니다.

## Tagging the release

이제 시간입니다! release-x.y 브랜치를 체크아웃하고 로컬 브랜치가 원격 브랜치와 최신 상태인지 확인하세요. 명령줄에서 다음을 실행하세요.

```
git tag v$(cat VERSION)
git push --tags
```

이것은 태그를 로컬에서 생성하고 GitHub에 푸시합니다.

릴리스를 태그한 후, 패치 번호를 증가시키고 끝에 `-pre`를 다시 추가하기 위해 release-x.y에 또 다른 PR을 제출하세요. 이는 브랜치 상태가 x.y 시리즈의 다음 포인트 릴리스의 프리릴리스 버전을 반영함을 나타냅니다.

Makefile의 나머지 지침을 따르십시오.

## Signing binaries

이 단계 중 일부는 보안 비밀번호가 필요합니다. 적절한 비밀번호를 얻으려면 Elliot Saba (staticfloat) 또는 Alex Arslan (ararslan)에게 문의하십시오. 각 플랫폼에 대한 코드 서명은 해당 플랫폼에서 수행해야 합니다(예: Windows 서명은 Windows에서 수행해야 함).

### Linux

코드 서명은 리눅스에서 수동으로 수행해야 하지만, 매우 간단합니다. 먼저 `juliasecure` AWS 버킷의 CodeSigning 폴더에서 `julia.key` 파일을 가져옵니다. 다음으로 이를 GnuPG 키링에 추가합니다.

```
gpg --import julia.key
```

이 작업을 수행하려면 Elliot 또는 Alex에게서 얻어야 하는 비밀번호를 입력해야 합니다. 다음으로, 키의 신뢰 수준을 최대값으로 설정합니다. `gpg` 세션을 시작하세요:

```
gpg --edit-key julia
```

프롬프트에 `trust`를 입력한 다음, 신뢰 수준을 묻는 질문이 나오면 가능한 최대값(아마도 5)을 입력하세요. GnuPG를 종료합니다.

이제 빌드봇에서 빌드된 각 Linux tarball에 대해 입력하세요.

```
gpg -u julia --armor --detach-sig julia-x.y.z-linux-<arch>.tar.gz
```

이것은 각 tarball에 대해 해당하는 .asc 파일을 생성합니다. 그게 전부입니다!

### macOS

코드 서명은 macOS 빌드봇에서 자동으로 이루어져야 합니다. 그러나 성공적으로 이루어졌는지 확인하는 것이 중요합니다. macOS를 실행하는 시스템이나 가상 머신에서 빌드봇에서 생성된 .dmg 파일을 다운로드합니다. 예를 들어, .dmg 파일의 이름이 `julia-x.y.z-osx.dmg`라고 가정해 보겠습니다. 다음 명령어를 실행합니다.

```
mkdir ./jlmnt
hdiutil mount -readonly -mountpoint ./jlmnt julia-x.y.z-osx.dmg
codesign -v jlmnt/Julia-x.y.app
```

마운트할 때 나열된 마운트된 디스크의 이름을 반드시 기록해 두세요! 예를 들어, 이것이 `disk3`라고 가정하겠습니다. 코드 서명 검증이 성공적으로 종료되면 `codesign` 단계에서 출력이 없습니다. 실제로 성공했다면 이제 .dmg를 분리할 수 있습니다:

```
hdiutil eject /dev/disk3
rm -rf ./jlmnt
```

메시지를 받으면 다음과 같은 내용이 포함될 수 있습니다.

> Julia-x.y.app: 코드 객체가 전혀 서명되지 않았습니다.


그럼 수동으로 서명해야 합니다.

수동으로 서명하려면 먼저 AWS의 `juliasecure` 버킷에 있는 CodeSigning 폴더에서 OS X 인증서를 가져옵니다. Keychain.app을 사용하여 .p12 파일을 키체인에 추가합니다. 키에 대한 비밀번호는 Elliot Saba(staticfloat) 또는 Alex Arslan(ararslan)에게 문의하세요. 이제 실행합니다.

```
hdiutil convert julia-x.y.z-osx.dmg -format UDRW -o julia-x.y.z-osx_writable.dmg
mkdir ./jlmnt
hdiutil mount -mountpoint julia-x.y.z-osx_writable.dmg
codesign -s "AFB379C0B4CBD9DB9A762797FC2AB5460A2B0DBE" --deep jlmnt/Julia-x.y.app
```

이것은 다음과 같은 메시지로 실패할 수 있습니다.

> Julia-x.y.app: 리소스 포크, Finder 정보 또는 유사한 잔여물은 허용되지 않습니다.


그렇다면 불필요한 속성을 제거해야 합니다:

```
xattr -cr jlmnt/Julia-x.y.app
```

그런 다음 코드 서명을 다시 시도하십시오. 오류가 발생하지 않으면 검증을 다시 시도하십시오. 모든 것이 잘 되었다면, 쓰기 가능한 .dmg를 마운트 해제하고 다시 읽기 전용으로 변환하십시오:

```
hdiutil eject /dev/disk3
rm -rf ./jlmnt
hdiutil convert julia-x.y.z-osx_writable.dmg -format UDZO -o julia-x.y.z-osx_fixed.dmg
```

결과 .dmg 파일이 실제로 수정되었는지 두 번 클릭하여 확인하세요. 모든 것이 괜찮다면, 이ject한 후 이름에서 `_fixed` 접미사를 제거하세요. 그게 전부입니다!

### Windows

서명은 Windows에서 수동으로 수행해야 합니다. 먼저 Microsoft 웹사이트에서 필요한 서명 유틸리티가 포함된 Windows 10 SDK를 다운로드합니다. `SignTool` 유틸리티가 필요하며, 이는 `C:\Program Files (x86)\Windows Kits\10\App Certification Kit`와 같은 위치에 설치되어 있어야 합니다. `juliasecure`의 CodeSigning에서 Windows 인증서 파일을 가져와 실행 파일과 동일한 디렉터리에 넣습니다. Windows CMD 창을 열고 모든 파일이 있는 위치로 `cd`한 후 실행합니다.

```
set PATH=%PATH%;C:\Program Files (x86)\Windows Kits\10\App Certification Kit;
signtool sign /f julia-windows-code-sign_2017.p12 /p "PASSWORD" ^
   /t http://timestamp.verisign.com/scripts/timstamp.dll ^
   /v julia-x.y.z-win32.exe
```

`^`는 Windows CMD에서 줄 계속하기 문자이며 `PASSWORD`는 이 인증서의 비밀번호를 위한 자리 표시자입니다. 항상처럼 비밀번호는 Elliot 또는 Alex에게 문의하세요. 오류가 없다면, 모든 것이 잘 진행된 것입니다!

## Uploading binaries

이제 모든 서명이 완료되었으므로, 이진 파일을 AWS에 업로드해야 합니다. Cyberduck과 같은 프로그램이나 `aws` 명령줄 유틸리티를 사용할 수 있습니다. 이진 파일은 적절한 폴더에 `julialang2` 버킷에 업로드해야 합니다. 예를 들어, Linux x86-64는 `julialang2/bin/linux/x.y`에 들어갑니다. 현재의 `julia-x.y-latest-linux-<arch>.tar.gz` 파일을 삭제하고 `julia-x.y.z-linux-<arch>.tar.gz`의 복사본으로 교체하는 것을 잊지 마세요.

우리는 또한 우리가 만든 모든 것, 즉 소스 tarball과 모든 릴리스 바이너리에 대한 체크섬을 업로드해야 합니다. 이것은 간단합니다:

```
shasum -a 256 julia-x.y.z* | grep -v -e sha256 -e md5 -e asc > julia-x.y.z.sha256
md5sum julia-x.y.z* | grep -v -e sha256 -e md5 -e asc > julia-x.y.z.md5
```

macOS에서 이러한 명령을 실행하는 경우 출력이 약간 다르게 나타나며, 기존 파일을 참조하여 형식을 조정할 수 있습니다. Mac 사용자는 `md5sum` 대신 `md5 -r`을 사용해야 합니다. .md5 및 .sha256 파일을 AWS의 `julialang2/bin/checksums`에 업로드하세요.

AWS에 업로드된 모든 파일의 권한이 "모두: 읽기"로 설정되어 있는지 확인하십시오.

업로드한 각 파일에 대해 Fastly 캐시를 삭제해야 웹사이트의 링크가 업데이트된 파일을 가리키도록 합니다. 예를 들어:

```
curl -X PURGE https://julialang-s3.julialang.org/bin/checksums/julia-x.y.z.sha256
```

때때로 이것이 필요하지는 않지만 그래도 하는 것이 좋습니다.
