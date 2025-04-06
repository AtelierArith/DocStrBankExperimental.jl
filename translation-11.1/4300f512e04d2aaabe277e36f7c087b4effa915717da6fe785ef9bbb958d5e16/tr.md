```
getalladdrinfo(host::AbstractString) -> Vector{IPAddr}
```

`host`'un tüm IP adreslerini alır. İşletim sisteminin temel `getaddrinfo` uygulamasını kullanır, bu da bir DNS sorgusu yapabilir.

# Örnekler

```julia-repl
julia> getalladdrinfo("google.com")
2-element Array{IPAddr,1}:
 ip"172.217.6.174"
 ip"2607:f8b0:4000:804::200e"
```
