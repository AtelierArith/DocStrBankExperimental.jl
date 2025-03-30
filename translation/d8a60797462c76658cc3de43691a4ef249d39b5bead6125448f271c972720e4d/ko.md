```
connect(manager::ClusterManager, pid::Int, config::WorkerConfig) -> (instrm::IO, outstrm::IO)
```

클러스터 관리자가 사용자 정의 전송을 사용하여 구현합니다. 이는 `config`에 의해 지정된 `pid`를 가진 작업자와의 논리적 연결을 설정하고 `IO` 객체 쌍을 반환해야 합니다. `pid`에서 현재 프로세스로의 메시지는 `instrm`에서 읽히고, `pid`로 전송될 메시지는 `outstrm`에 기록됩니다. 사용자 정의 전송 구현은 메시지가 완전하고 순서대로 전달되고 수신되도록 보장해야 합니다. `connect(manager::ClusterManager.....)`는 작업자 간의 TCP/IP 소켓 연결을 설정합니다.
