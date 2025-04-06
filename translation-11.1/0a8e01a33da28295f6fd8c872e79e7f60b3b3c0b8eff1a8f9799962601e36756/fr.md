```
TCPSocket(; delay=true)
```

Ouvre un socket TCP en utilisant libuv. Si `delay` est vrai, libuv retarde la création du descripteur de fichier du socket jusqu'à la première appel de [`bind`](@ref). `TCPSocket` a divers champs pour indiquer l'état du socket ainsi que ses tampons d'envoi/réception.
