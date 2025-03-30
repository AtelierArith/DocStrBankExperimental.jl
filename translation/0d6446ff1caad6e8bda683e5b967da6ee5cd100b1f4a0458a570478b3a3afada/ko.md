```
getipaddr() -> IPAddr
```

로컬 머신의 IP 주소를 가져오며, IPv4를 IPv6보다 우선시합니다. 주소가 없으면 예외를 발생시킵니다.

```
getipaddr(addr_type::Type{T}) where T<:IPAddr -> T
```

지정된 유형의 로컬 머신의 IP 주소를 가져옵니다. 지정된 유형의 주소가 없으면 예외를 발생시킵니다.

이 함수는 [`getipaddrs`](@ref)에 대한 하위 호환성 래퍼입니다. 새로운 애플리케이션은 대신 [`getipaddrs`](@ref)를 사용해야 합니다.

# 예제

```julia-repl
julia> getipaddr()
ip"192.168.1.28"

julia> getipaddr(IPv6)
ip"fe80::9731:35af:e1c5:6e49"
```

또한 [`getipaddrs`](@ref)를 참조하십시오.
