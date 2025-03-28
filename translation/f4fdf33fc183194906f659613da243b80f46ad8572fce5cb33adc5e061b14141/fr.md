```
setopt(sock::UDPSocket; multicast_loop=nothing, multicast_ttl=nothing, enable_broadcast=nothing, ttl=nothing)
```

Définir les options du socket UDP.

  * `multicast_loop`: boucle pour les paquets multicast (par défaut : `true`).
  * `multicast_ttl`: TTL pour les paquets multicast (par défaut : `nothing`).
  * `enable_broadcast`: le drapeau doit être défini sur `true` si le socket sera utilisé pour des messages de diffusion, sinon le système UDP renverra une erreur d'accès (par défaut : `false`).
  * `ttl`: Durée de vie des paquets envoyés sur le socket (par défaut : `nothing`).
