```
process_messages(r_stream::IO, w_stream::IO, incoming::Bool=true)
```

Wird von Cluster-Managern mit benutzerdefinierten Transporten aufgerufen. Es sollte aufgerufen werden, wenn die benutzerdefinierte Transportimplementierung die erste Nachricht von einem entfernten Worker erhält. Der benutzerdefinierte Transport muss eine logische Verbindung zum entfernten Worker verwalten und zwei `IO`-Objekte bereitstellen, eines für eingehende Nachrichten und das andere für an den entfernten Worker adressierte Nachrichten. Wenn `incoming` `true` ist, hat der entfernte Peer die Verbindung initiiert. Derjenige, der die Verbindung initiiert, sendet das Cluster-Cookie und seine Julia-Versionnummer, um den Authentifizierungs-Handschlag durchzuführen.

Siehe auch [`cluster_cookie`](@ref).
