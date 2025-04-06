```
worker_id_from_socket(s) -> pid
```

Eine Low-Level-API, die, gegeben eine `IO`-Verbindung oder einen `Worker`, die `pid` des Workers zurückgibt, mit dem sie verbunden ist. Dies ist nützlich, wenn benutzerdefinierte [`serialize`](@ref) Methoden für einen Typ geschrieben werden, die die geschriebenen Daten je nach Prozess-ID des empfangenden Prozesses optimieren.
