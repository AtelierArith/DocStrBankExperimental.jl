```
channel_from_id(id) -> c
```

Une API de bas niveau qui retourne le `AbstractChannel` de support pour un `id` retourné par [`remoteref_id`](@ref). L'appel est valide uniquement sur le nœud où le canal de support existe.
