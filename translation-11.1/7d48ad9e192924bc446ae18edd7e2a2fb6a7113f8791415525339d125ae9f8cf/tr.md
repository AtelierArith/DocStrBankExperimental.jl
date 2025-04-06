```
getipaddrs(addr_type::Type{T}=IPAddr; loopback::Bool=false) where T<:IPAddr -> Vector{T}
```

Yerel makinenin IP adreslerini alır.

İsteğe bağlı `addr_type` parametresini `IPv4` veya `IPv6` olarak ayarlamak, yalnızca o türdeki adreslerin döndürülmesini sağlar.

`loopback` anahtar argümanı, döngüsel adreslerin (örneğin `ip"127.0.0.1"`, `ip"::1"`) dahil edilip edilmeyeceğini belirler.

!!! compat "Julia 1.2"
    Bu fonksiyon Julia 1.2 itibarıyla mevcuttur.


# Örnekler

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

Ayrıca [`islinklocaladdr`](@ref) bakınız.
