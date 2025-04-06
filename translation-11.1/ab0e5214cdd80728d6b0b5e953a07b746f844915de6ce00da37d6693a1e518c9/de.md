```
listenany([host::IPAddr,] port_hint; backlog::Integer=BACKLOG_DEFAULT) -> (UInt16, TCPServer)
```

Erstellt einen `TCPServer` auf einem beliebigen Port, wobei der Hinweis als Ausgangspunkt verwendet wird. Gibt ein Tupel des tatsächlichen Ports zurück, auf dem der Server erstellt wurde, und den Server selbst. Das Argument backlog definiert die maximale Länge, die die Warteschlange ausstehender Verbindungen für sockfd erreichen kann.
