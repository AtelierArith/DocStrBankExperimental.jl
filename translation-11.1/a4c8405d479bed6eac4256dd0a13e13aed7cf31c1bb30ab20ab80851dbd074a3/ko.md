```
poll_fd(fd, timeout_s::Real=-1; readable=false, writable=false)
```

파일 디스크립터 `fd`의 읽기 또는 쓰기 가능성의 변화를 모니터링하며, `timeout_s` 초로 주어진 타임아웃을 설정합니다.

키워드 인자는 읽기 및/또는 쓰기 상태 중 어떤 것을 모니터링할지를 결정하며, 이 중 적어도 하나는 `true`로 설정되어야 합니다.

반환되는 값은 불리언 필드 `readable`, `writable`, 및 `timedout`을 가진 객체로, 폴링의 결과를 제공합니다.
