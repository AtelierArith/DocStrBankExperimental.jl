```
approve(payload::CredentialPayload; shred::Bool=true) -> Nothing
```

Almacena la credencial `payload` para su reutilización en una futura autenticación. Solo debe ser llamado cuando la autenticación haya sido exitosa.

La palabra clave `shred` controla si la información sensible en el campo de credencial del payload debe ser destruida. Solo debe establecerse en `false` durante las pruebas.
