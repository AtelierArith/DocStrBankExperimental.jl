```
@ip_str str -> IPAddr
```

`str`를 IP 주소로 파싱합니다.

# 예시

```jldoctest
julia> ip"127.0.0.1"
ip"127.0.0.1"

julia> @ip_str "2001:db8:0:0:0:0:2:1"
ip"2001:db8::2:1"
```
