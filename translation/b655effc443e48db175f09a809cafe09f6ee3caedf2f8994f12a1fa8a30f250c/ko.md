```
LOAD_PATH
```

`using` 및 `import` 문을 고려할 프로젝트 환경 또는 패키지 디렉토리에 대한 경로 배열입니다. 설정된 경우 [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) 환경 변수를 기반으로 채워지며, 그렇지 않으면 기본값은 `["@", "@v#.#", "@stdlib"]`입니다. `@`로 시작하는 항목은 특별한 의미를 가집니다:

  * `@`는 "현재 활성 환경"을 나타내며, 초기 값은 [`JULIA_PROJECT`](@ref JULIA_PROJECT) 환경 변수 또는 `--project` 명령줄 옵션에 의해 처음 결정됩니다.
  * `@stdlib`은 현재 Julia 설치의 표준 라이브러리 디렉토리의 절대 경로로 확장됩니다.
  * `@name`은 이름이 지정된 환경을 나타내며, 이는 `environments` 하위 디렉토리 아래의 저장소에 저장됩니다 (자세한 내용은 [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) 참조). 사용자의 이름이 지정된 환경은 `~/.julia/environments`에 저장되므로 `@name`은 `~/.julia/environments/name`에 해당하는 환경을 참조하며, 해당 환경이 존재하고 `Project.toml` 파일을 포함하고 있다면 참조됩니다. `name`에 `#` 문자가 포함되어 있으면, 이는 Julia 버전 번호의 주요, 부, 패치 구성 요소로 대체됩니다. 예를 들어, Julia 1.2를 실행 중이라면 `@v#.#`는 `@v1.2`로 확장되며, 일반적으로 `~/.julia/environments/v1.2`에서 해당 이름의 환경을 찾습니다.

프로젝트 및 패키지를 검색하는 `LOAD_PATH`의 완전히 확장된 값은 `Base.load_path()` 함수를 호출하여 확인할 수 있습니다.

또한 [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH), [`JULIA_PROJECT`](@ref JULIA_PROJECT), [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH), 및 [Code Loading](@ref code-loading)을 참조하십시오.
