```
IPv4(host::Integer) -> IPv4
```

IP 주소 `host`에서 [`Integer`](@ref) 형식으로 IPv4 객체를 반환합니다.

# 예제

```jldoctest
julia> IPv4(3223256218)
ip"192.30.252.154"
```
