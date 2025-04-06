```
getipaddrs(addr_type::Type{T}=IPAddr; loopback::Bool=false) where T<:IPAddr -> Vector{T}
```

로컬 머신의 IP 주소를 가져옵니다.

선택적 `addr_type` 매개변수를 `IPv4` 또는 `IPv6`로 설정하면 해당 유형의 주소만 반환됩니다.

`loopback` 키워드 인자는 루프백 주소(예: `ip"127.0.0.1"`, `ip"::1"`)가 포함될지 여부를 결정합니다.

!!! compat "Julia 1.2"
    이 함수는 Julia 1.2부터 사용할 수 있습니다.


# 예제

```julia-repl
julia> getipaddrs()
5-element Array{IPAddr,1}:
 ip"198.51.100.17"
 ip"203.0.113.2"
 ip"2001:db8:8:4:445e:5fff:fe5d:5500"
 ip"2001:db8:8:4:c164:402e:7e3c:3668"
 ip"fe80::445e:5fff:fe5d:5500"

julia> getipaddrs(IPv6)
3-element Array{IPv6,1}:
 ip"2001:db8:8:4:445e:5fff:fe5d:5500"
 ip"2001:db8:8:4:c164:402e:7e3c:3668"
 ip"fe80::445e:5fff:fe5d:5500"
```

또한 [`islinklocaladdr`](@ref)를 참조하세요.
