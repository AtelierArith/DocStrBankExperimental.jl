```
relpath(path::AbstractString, startpath::AbstractString = ".") -> String
```

현재 디렉토리 또는 선택적 시작 디렉토리에서 `path`에 대한 상대 파일 경로를 반환합니다. 이는 경로 계산입니다: `path` 또는 `startpath`의 존재 여부나 성격을 확인하기 위해 파일 시스템에 접근하지 않습니다.

Windows에서는 드라이브 문자를 제외한 경로의 모든 부분에 대해 대소문자 구분이 적용됩니다. `path`와 `startpath`가 서로 다른 드라이브를 참조하는 경우, `path`의 절대 경로가 반환됩니다.
