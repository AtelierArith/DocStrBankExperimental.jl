```
process_messages(r_stream::IO, w_stream::IO, incoming::Bool=true)
```

Llamado por los administradores de clúster utilizando transportes personalizados. Debe ser llamado cuando la implementación del transporte personalizado recibe el primer mensaje de un trabajador remoto. El transporte personalizado debe gestionar una conexión lógica con el trabajador remoto y proporcionar dos objetos `IO`, uno para los mensajes entrantes y el otro para los mensajes dirigidos al trabajador remoto. Si `incoming` es `true`, el par remoto inició la conexión. Cualquiera de los dos que inicie la conexión envía la cookie del clúster y su número de versión de Julia para realizar el apretón de manos de autenticación.

Véase también [`cluster_cookie`](@ref).
