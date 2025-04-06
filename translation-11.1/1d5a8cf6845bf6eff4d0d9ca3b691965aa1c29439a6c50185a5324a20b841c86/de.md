```
islinklocaladdr(addr::IPAddr)
```

Überprüft, ob eine IP-Adresse eine Link- lokale Adresse ist. Link-lokale Adressen sind nicht garantiert, über ihr Netzwerksegment hinaus einzigartig zu sein, daher leiten Router sie nicht weiter. Link-lokale Adressen stammen aus den Adressblöcken `169.254.0.0/16` oder `fe80::/10`.

# Beispiele

```julia
filter(!islinklocaladdr, getipaddrs())
```
