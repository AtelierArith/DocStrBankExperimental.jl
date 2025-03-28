```
islinklocaladdr(addr::IPAddr)
```

Teste si une adresse IP est une adresse locale de lien. Les adresses locales de lien ne sont pas garanties d'être uniques au-delà de leur segment de réseau, par conséquent, les routeurs ne les transmettent pas. Les adresses locales de lien proviennent des blocs d'adresses `169.254.0.0/16` ou `fe80::/10`.

# Exemples

```julia
filter(!islinklocaladdr, getipaddrs())
```
