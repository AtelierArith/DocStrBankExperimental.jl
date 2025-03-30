```
set_peek_duration(t::Float64)
```

프로파일 "peek"의 지속 시간을 초 단위로 설정합니다. 이 프로파일은 플랫폼에 따라 `SIGINFO` 또는 `SIGUSR1`을 통해 트리거됩니다.
