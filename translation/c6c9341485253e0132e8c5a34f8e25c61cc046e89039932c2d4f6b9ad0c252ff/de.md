```
ssh_key_name() :: String
```

Die Funktion `ssh_key_name()` gibt den Basisnamen der Schlüsseldateien zurück, die SSH beim Herstellen einer Verbindung verwenden sollte. Es gibt normalerweise keinen Grund, warum diese Funktion direkt aufgerufen werden sollte, und Bibliotheken sollten im Allgemeinen die Funktionen `ssh_key_path` und `ssh_pub_key_path` verwenden, um vollständige Pfade zu erhalten. Wenn die Umgebungsvariable `SSH_KEY_NAME` gesetzt ist, gibt diese Funktion diesen Wert zurück; andernfalls gibt sie standardmäßig `id_rsa` zurück.
