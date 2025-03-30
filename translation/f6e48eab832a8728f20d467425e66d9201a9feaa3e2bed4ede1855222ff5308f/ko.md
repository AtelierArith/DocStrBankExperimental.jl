```
splitdrive(path::AbstractString) -> (AbstractString, AbstractString)
```

Windows에서는 경로를 드라이브 문자 부분과 경로 부분으로 나눕니다. Unix 시스템에서는 첫 번째 구성 요소가 항상 빈 문자열입니다.
