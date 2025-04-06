```
include_dependency(path::AbstractString; track_content::Bool=true)
```

모듈에서 `path`로 지정된 파일, 디렉토리 또는 심볼릭 링크(상대 경로 또는 절대 경로)가 사전 컴파일을 위한 의존성임을 선언합니다. 즉, `track_content=true`인 경우 `path`의 내용이 변경되면 모듈을 다시 컴파일해야 합니다(만약 `path`가 디렉토리인 경우 내용은 `join(readdir(path))`와 같습니다). `track_content=false`인 경우 `path`의 수정 시간 `mtime`이 변경될 때 다시 컴파일이 트리거됩니다.

이는 모듈이 [`include`](@ref)를 통해 사용되지 않는 경로에 의존하는 경우에만 필요합니다. 컴파일 외부에서는 아무런 효과가 없습니다.

!!! compat "Julia 1.11"
    키워드 인수 `track_content`는 최소한 Julia 1.11이 필요합니다. `path`가 읽을 수 없는 경우 오류가 발생합니다.

