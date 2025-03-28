```
approve(payload::CredentialPayload; shred::Bool=true) -> Nothing
```

Speichert die `payload`-Anmeldeinformationen zur Wiederverwendung bei einer zukünftigen Authentifizierung. Sollte nur aufgerufen werden, wenn die Authentifizierung erfolgreich war.

Das Schlüsselwort `shred` steuert, ob sensible Informationen im Anmeldeinformationsfeld des Payloads zerstört werden sollen. Sollte nur während des Testens auf `false` gesetzt werden.
