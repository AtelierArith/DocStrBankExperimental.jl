```
getaddrinfo(host::AbstractString) -> IPAddr
```

Erhält die erste verfügbare IP-Adresse von `host`, die entweder eine `IPv4`- oder `IPv6`-Adresse sein kann. Verwendet die zugrunde liegende getaddrinfo-Implementierung des Betriebssystems, die möglicherweise eine DNS-Abfrage durchführt.
