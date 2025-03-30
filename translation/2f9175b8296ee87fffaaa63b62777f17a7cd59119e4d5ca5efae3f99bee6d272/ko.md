```
DEPOT_PATH
```

패키지 관리자와 줄리아의 코드 로딩 메커니즘이 패키지 레지스트리, 설치된 패키지, 명명된 환경, 리포지토리 클론, 캐시된 컴파일된 패키지 이미지 및 구성 파일을 찾는 "depot" 위치의 스택입니다. 기본적으로 다음을 포함합니다:

1. `~/.julia` 여기서 `~`는 시스템에 적합한 사용자 홈입니다;
2. 아키텍처별 공유 시스템 디렉토리, 예: `/usr/local/share/julia`;
3. 아키텍처 독립적인 공유 시스템 디렉토리, 예: `/usr/share/julia`.

따라서 `DEPOT_PATH`는 다음과 같을 수 있습니다:

```julia
[joinpath(homedir(), ".julia"), "/usr/local/share/julia", "/usr/share/julia"]
```

첫 번째 항목은 "사용자 depot"이며 현재 사용자가 쓸 수 있고 소유해야 합니다. 사용자 depot는 다음과 같은 작업이 이루어지는 곳입니다: 레지스트리가 클론되고, 새로운 패키지 버전이 설치되며, 명명된 환경이 생성되고 업데이트되고, 패키지 리포가 클론되며, 새로 컴파일된 패키지 이미지 파일이 저장되고, 로그 파일이 작성되며, 개발 패키지가 기본적으로 체크아웃되고, 전역 구성 데이터가 저장됩니다. depot 경로의 이후 항목은 읽기 전용으로 처리되며 시스템 관리자가 설치하고 관리하는 레지스트리, 패키지 등에 적합합니다.

`DEPOT_PATH`는 설정된 경우 [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) 환경 변수를 기반으로 채워집니다.

## DEPOT_PATH 내용

`DEPOT_PATH`의 각 항목은 줄리아가 다양한 목적으로 사용하는 하위 디렉토리를 포함하는 디렉토리에 대한 경로입니다. 다음은 depot에 존재할 수 있는 일부 하위 디렉토리에 대한 개요입니다:

  * `artifacts`: 패키지가 설치 관리를 위해 사용하는 콘텐츠를 포함합니다.
  * `clones`: 패키지 리포의 전체 클론을 포함합니다. `Pkg.jl`에 의해 유지되며 캐시로 사용됩니다.
  * `config`: `startup.jl`과 같은 줄리아 수준의 구성을 포함합니다.
  * `compiled`: 패키지에 대한 미리 컴파일된 `*.ji` 파일을 포함합니다. 줄리아에 의해 유지됩니다.
  * `dev`: `Pkg.develop`의 기본 디렉토리입니다. `Pkg.jl`과 사용자에 의해 유지됩니다.
  * `environments`: 기본 패키지 환경입니다. 예를 들어 특정 줄리아 버전의 전역 환경입니다. `Pkg.jl`에 의해 유지됩니다.
  * `logs`: `Pkg` 및 `REPL` 작업의 로그를 포함합니다. `Pkg.jl`과 `Julia`에 의해 유지됩니다.
  * `packages`: 패키지를 포함하며, 일부는 명시적으로 설치되었고 일부는 암묵적 종속성입니다. `Pkg.jl`에 의해 유지됩니다.
  * `registries`: 패키지 레지스트리를 포함합니다. 기본적으로는 `General`만 포함됩니다. `Pkg.jl`에 의해 유지됩니다.
  * `scratchspaces`: 패키지가 [`Scratch.jl`](https://github.com/JuliaPackaging/Scratch.jl) 패키지를 통해 설치하는 콘텐츠를 포함합니다. `Pkg.gc()`는 사용되지 않는 것으로 알려진 콘텐츠를 삭제합니다.

!!! note
    콘텐츠를 저장하려는 패키지는 depot 루트에 새로운 하위 디렉토리를 생성하는 대신 [`Scratch.jl`](https://github.com/JuliaPackaging/Scratch.jl) 를 통해 `scratchspaces` 하위 디렉토리를 사용해야 합니다.


또한 [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) 및 [Code Loading](@ref code-loading)을 참조하십시오.
