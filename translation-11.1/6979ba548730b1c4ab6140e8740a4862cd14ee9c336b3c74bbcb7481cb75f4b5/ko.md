```
getaddrinfo(host::AbstractString) -> IPAddr
```

`host`의 첫 번째 사용 가능한 IP 주소를 가져옵니다. 이 주소는 `IPv4` 또는 `IPv6` 주소일 수 있습니다. 운영 체제의 기본 getaddrinfo 구현을 사용하며, 이 구현은 DNS 조회를 수행할 수 있습니다.
