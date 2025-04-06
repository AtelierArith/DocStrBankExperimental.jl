```
reject(payload::CredentialPayload; shred::Bool=true) -> Nothing
```

Verwerfen Sie das `payload`-Credential, um eine Wiederverwendung bei zukünftigen Authentifizierungen zu verhindern. Sollte nur aufgerufen werden, wenn die Authentifizierung nicht erfolgreich war.

Das `shred`-Schlüsselwort steuert, ob sensible Informationen im Feld des Payload-Credentials zerstört werden sollen. Sollte nur während des Testens auf `false` gesetzt werden.
