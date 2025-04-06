```
mkfifo(path::AbstractString, [mode::Integer]) -> path
```

지정된 `path`에 FIFO 특수 파일(이름이 있는 파이프)을 만듭니다. 성공 시 `path`를 그대로 반환합니다.

`mkfifo`는 Unix 플랫폼에서만 지원됩니다.

!!! compat "Julia 1.11"
    `mkfifo`는 최소한 Julia 1.11이 필요합니다.

