```
require(into::Module, module::Symbol)
```

이 함수는 모듈이 `Main`에 이미 정의되어 있지 않은 경우 [`using`](@ref) / [`import`](@ref) 구현의 일부입니다. 또한 모듈이 이전에 로드되었는지 여부에 관계없이 모듈을 강제로 다시 로드하기 위해 직접 호출할 수 있습니다(예: 라이브러리를 대화식으로 개발할 때).

활성 노드에서 `Main` 모듈의 컨텍스트 내에서 소스 파일을 로드하며, 파일에 대한 표준 위치를 검색합니다. `require`는 최상위 작업으로 간주되므로 현재 `include` 경로를 설정하지만 파일 검색에 사용하지는 않습니다(자세한 내용은 [`include`](@ref) 도움말 참조). 이 함수는 일반적으로 라이브러리 코드를 로드하는 데 사용되며, 패키지를 로드하기 위해 `using`에 의해 암묵적으로 호출됩니다.

파일을 검색할 때, `require`는 먼저 전역 배열 [`LOAD_PATH`](@ref)에서 패키지 코드를 찾습니다. `require`는 모든 플랫폼에서 대소문자를 구분하며, macOS 및 Windows와 같은 대소문자를 구분하지 않는 파일 시스템에서도 마찬가지입니다.

코드 로딩에 대한 자세한 내용은 [모듈](@ref modules) 및 [병렬 컴퓨팅](@ref code-availability)에 대한 매뉴얼 섹션을 참조하십시오.
