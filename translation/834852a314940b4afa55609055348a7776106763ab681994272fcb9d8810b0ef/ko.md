```
bind(socket::Union{TCPServer, UDPSocket, TCPSocket}, host::IPAddr, port::Integer; ipv6only=false, reuseaddr=false, kws...)
```

`socket`을 주어진 `host:port`에 바인딩합니다. `0.0.0.0`은 모든 장치에서 수신 대기합니다.

  * `ipv6only` 매개변수는 이중 스택 모드를 비활성화합니다. `ipv6only=true`인 경우, IPv6 스택만 생성됩니다.
  * `reuseaddr=true`인 경우, 여러 스레드나 프로세스가 모두 `reuseaddr=true`로 설정하면 동일한 주소에 바인딩할 수 있지만, 마지막으로 바인딩한 것만 트래픽을 수신합니다.
