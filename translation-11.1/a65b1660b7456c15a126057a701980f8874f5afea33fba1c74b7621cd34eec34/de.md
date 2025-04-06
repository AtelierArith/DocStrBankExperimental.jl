```
getnameinfo(host::IPAddr) -> String
```

Führt eine Rückwärtssuche für die IP-Adresse durch, um einen Hostnamen und einen Dienst unter Verwendung der zugrunde liegenden `getnameinfo`-Implementierung des Betriebssystems zurückzugeben.

# Beispiele

```julia-repl
julia> getnameinfo(IPv4("8.8.8.8"))
"google-public-dns-a.google.com"
```
