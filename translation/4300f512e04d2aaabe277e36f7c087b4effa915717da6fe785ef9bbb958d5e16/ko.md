```
getalladdrinfo(host::AbstractString) -> Vector{IPAddr}
```

`host`의 모든 IP 주소를 가져옵니다. 운영 체제의 기본 `getaddrinfo` 구현을 사용하며, 이는 DNS 조회를 수행할 수 있습니다.

# 예제

```julia-repl
julia> getalladdrinfo("google.com")
2-element Array{IPAddr,1}:
 ip"172.217.6.174"
 ip"2607:f8b0:4000:804::200e"
```
