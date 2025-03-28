```
islinklocaladdr(addr::IPAddr)
```

Prueba si una dirección IP es una dirección local de enlace. Las direcciones locales de enlace no garantizan ser únicas más allá de su segmento de red, por lo tanto, los enrutadores no las reenvían. Las direcciones locales de enlace provienen de los bloques de direcciones `169.254.0.0/16` o `fe80::/10`.

# Ejemplos

```julia
filter(!islinklocaladdr, getipaddrs())
```
