```
islinklocaladdr(addr::IPAddr)
```

IP 주소가 링크 로컬 주소인지 테스트합니다. 링크 로컬 주소는 네트워크 세그먼트를 넘어서는 고유성이 보장되지 않으므로 라우터가 이를 전달하지 않습니다. 링크 로컬 주소는 주소 블록 `169.254.0.0/16` 또는 `fe80::/10`에서 나옵니다.

# 예제

```julia
filter(!islinklocaladdr, getipaddrs())
```
