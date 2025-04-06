```
abspath(path::AbstractString, paths::AbstractString...) -> String
```

경로 집합을 절대 경로로 변환하여 함께 결합하고 필요한 경우 현재 디렉토리를 추가합니다. `abspath(joinpath(path, paths...))`와 동일합니다.
