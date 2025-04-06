```
getaddrinfo(host::AbstractString, IPAddr) -> IPAddr
```

지정된 `IPAddr` 유형의 `host`의 첫 번째 IP 주소를 가져옵니다. 운영 체제의 기본 getaddrinfo 구현을 사용하며, 이는 DNS 조회를 수행할 수 있습니다.

# 예제

```julia-repl
julia> getaddrinfo("localhost", IPv6)
ip"::1"

julia> getaddrinfo("localhost", IPv4)
ip"127.0.0.1"
```
