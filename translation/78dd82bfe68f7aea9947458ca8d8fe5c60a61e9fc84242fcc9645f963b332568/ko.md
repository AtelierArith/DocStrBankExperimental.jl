```
IPv6(host::Integer) -> IPv6
```

IP 주소 `host`를 [`Integer`](@ref) 형식으로 변환하여 IPv6 객체를 반환합니다.

# 예제

```jldoctest
julia> IPv6(3223256218)
ip"::c01e:fc9a"
```
