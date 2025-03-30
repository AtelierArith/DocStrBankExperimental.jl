```
getnameinfo(host::IPAddr) -> String
```

IP 주소에 대한 역 조회를 수행하여 운영 체제의 기본 `getnameinfo` 구현을 사용하여 호스트 이름과 서비스를 반환합니다.

# 예제

```julia-repl
julia> getnameinfo(IPv4("8.8.8.8"))
"google-public-dns-a.google.com"
```
