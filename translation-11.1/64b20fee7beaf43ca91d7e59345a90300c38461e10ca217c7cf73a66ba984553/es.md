```
reject(payload::CredentialPayload; shred::Bool=true) -> Nothing
```

Descarta la credencial `payload` para que no se vuelva a utilizar en futuras autenticaciones. Solo debe ser llamado cuando la autenticación no fue exitosa.

La palabra clave `shred` controla si la información sensible en el campo de credenciales del payload debe ser destruida. Solo debe establecerse en `false` durante las pruebas.
