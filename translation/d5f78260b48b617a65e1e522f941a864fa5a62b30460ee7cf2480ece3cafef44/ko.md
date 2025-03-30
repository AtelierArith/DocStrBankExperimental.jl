```
start_worker([out::IO=stdout], cookie::AbstractString=readline(stdin); close_stdin::Bool=true, stderr_to_stdout::Bool=true)
```

`start_worker`는 TCP/IP를 통해 연결되는 작업자 프로세스의 기본 진입점인 내부 함수입니다. 이 함수는 프로세스를 Julia 클러스터 작업자로 설정합니다.

호스트:포트 정보는 스트림 `out`에 기록됩니다(기본값은 stdout).

이 함수는 필요할 경우 stdin에서 쿠키를 읽고, 사용 가능한 포트에서 수신 대기하며(또는 지정된 경우 `--bind-to` 명령줄 옵션의 포트에서) 들어오는 TCP 연결 및 요청을 처리할 작업을 예약합니다. 또한 (선택적으로) stdin을 닫고 stderr를 stdout으로 리디렉션합니다.

반환하지 않습니다.
