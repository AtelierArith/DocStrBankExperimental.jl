```
connect(manager::ClusterManager, pid::Int, config::WorkerConfig) -> (instrm::IO, outstrm::IO)
```

Implementiert von Cluster-Managern mit benutzerdefinierten Transporten. Es sollte eine logische Verbindung zum Worker mit der ID `pid`, die durch `config` angegeben ist, hergestellt werden und ein Paar von `IO`-Objekten zurückgeben. Nachrichten von `pid` an den aktuellen Prozess werden von `instrm` gelesen, während Nachrichten, die an `pid` gesendet werden sollen, in `outstrm` geschrieben werden. Die Implementierung des benutzerdefinierten Transports muss sicherstellen, dass Nachrichten vollständig und in der richtigen Reihenfolge zugestellt und empfangen werden. `connect(manager::ClusterManager.....)` richtet TCP/IP-Socket-Verbindungen zwischen den Workern ein.
