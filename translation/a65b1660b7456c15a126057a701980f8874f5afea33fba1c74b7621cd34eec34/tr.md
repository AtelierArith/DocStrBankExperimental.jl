```
getnameinfo(host::IPAddr) -> String
```

IP adresi için ters arama yaparak işletim sisteminin temel `getnameinfo` uygulamasını kullanarak bir ana bilgisayar adı ve hizmet döndürür.

# Örnekler

```julia-repl
julia> getnameinfo(IPv4("8.8.8.8"))
"google-public-dns-a.google.com"
```
