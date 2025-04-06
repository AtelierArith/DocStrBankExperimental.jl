```
normpath(path::AbstractString, paths::AbstractString...) -> String
```

여러 경로를 결합하고 "." 및 ".." 항목을 제거하여 정규화된 경로로 변환합니다. `normpath(joinpath(path, paths...))`와 동일합니다.
