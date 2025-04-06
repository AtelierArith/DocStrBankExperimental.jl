```
link_pipe!(pipe; reader_supports_async=false, writer_supports_async=false)
```

`pipe`를 초기화하고 `in` 엔드포인트를 `out` 엔드포인트에 연결합니다. 키워드 인수 `reader_supports_async`/`writer_supports_async`는 Windows의 `OVERLAPPED` 및 POSIX 시스템의 `O_NONBLOCK`에 해당합니다. 외부 프로그램(예: [`run`](@ref)으로 실행된 명령의 출력)에서 사용되지 않는 한 `true`여야 합니다.
