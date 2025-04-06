```
find_artifacts_toml(path::String)
```

주어진 `.jl` 파일의 경로(예: 매크로 컨텍스트에서 `__source__.file`에 의해 반환된 경로)를 사용하여 포함된 프로젝트 내에 있는 `(Julia)Artifacts.toml`을 찾습니다(존재하는 경우). 그렇지 않으면 `nothing`을 반환합니다.

!!! compat "Julia 1.3"
    이 함수는 최소한 Julia 1.3이 필요합니다.

