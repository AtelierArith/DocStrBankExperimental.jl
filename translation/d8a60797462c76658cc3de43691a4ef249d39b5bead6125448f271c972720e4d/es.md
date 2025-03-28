```
connect(manager::ClusterManager, pid::Int, config::WorkerConfig) -> (instrm::IO, outstrm::IO)
```

Implementado por administradores de clúster utilizando transportes personalizados. Debe establecer una conexión lógica con el trabajador con id `pid`, especificado por `config` y devolver un par de objetos `IO`. Los mensajes de `pid` al proceso actual se leerán de `instrm`, mientras que los mensajes que se enviarán a `pid` se escribirán en `outstrm`. La implementación del transporte personalizado debe garantizar que los mensajes se entreguen y reciban completamente y en orden. `connect(manager::ClusterManager.....)` establece conexiones de socket TCP/IP entre los trabajadores.
