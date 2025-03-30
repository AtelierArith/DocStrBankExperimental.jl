```
getipaddr() -> IPAddr
```

Yerel makinenin IP adresini alır, IPv4'ü IPv6'ya tercih eder. Hiçbir adres mevcut değilse hata fırlatır.

```
getipaddr(addr_type::Type{T}) where T<:IPAddr -> T
```

Belirtilen türdeki yerel makinenin IP adresini alır. Belirtilen türde hiç adres mevcut değilse hata fırlatır.

Bu fonksiyon, [`getipaddrs`](@ref) etrafında bir geriye uyumluluk sarmalayıcısıdır. Yeni uygulamalar bunun yerine [`getipaddrs`](@ref) kullanmalıdır.

# Örnekler

```julia-repl
julia> getipaddr()
ip"192.168.1.28"

julia> getipaddr(IPv6)
ip"fe80::9731:35af:e1c5:6e49"
```

Ayrıca bkz. [`getipaddrs`](@ref).
