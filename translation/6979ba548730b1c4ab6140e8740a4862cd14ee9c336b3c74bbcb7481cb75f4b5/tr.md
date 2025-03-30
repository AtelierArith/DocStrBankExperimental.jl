```
getaddrinfo(host::AbstractString) -> IPAddr
```

`host`'ün ilk mevcut IP adresini alır; bu, ya bir `IPv4` ya da bir `IPv6` adresi olabilir. İşletim sisteminin temel getaddrinfo uygulamasını kullanır; bu, bir DNS sorgusu yapabilir.
