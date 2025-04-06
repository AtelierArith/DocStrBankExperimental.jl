```
TCPSocket(; delay=true)
```

libuv를 사용하여 TCP 소켓을 엽니다. `delay`가 true인 경우, libuv는 첫 번째 [`bind`](@ref) 호출까지 소켓의 파일 디스크립터 생성을 지연시킵니다. `TCPSocket`은 소켓의 상태와 전송/수신 버퍼를 나타내는 다양한 필드를 가지고 있습니다.
