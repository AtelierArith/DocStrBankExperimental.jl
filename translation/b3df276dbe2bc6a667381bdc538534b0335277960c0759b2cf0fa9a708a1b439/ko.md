```
Base.isprecompiled(pkg::PkgId; ignore_loaded::Bool=false)
```

주어진 PkgId가 활성 프로젝트 내에서 미리 컴파일되었는지 여부를 반환합니다.

기본적으로 이 검사는 현재 로드된 종속성의 서로 다른 버전이 예상되는 것과 관련하여 코드 로딩이 수행되는 방식을 관찰합니다. 로드된 모듈을 무시하고 새 줄리아 세션에서와 같이 대답하려면 `ignore_loaded=true`를 지정하십시오.

!!! compat "Julia 1.10"
    이 함수는 최소한 Julia 1.10이 필요합니다.

