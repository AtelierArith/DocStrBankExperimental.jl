```
listen(path::AbstractString) -> PipeServer
```

이름이 있는 파이프 / UNIX 도메인 소켓을 생성하고 수신합니다.

!!! note
    Unix에서 경로 길이는 92바이트에서 108바이트 사이로 제한됩니다 (cf. `man unix`).

