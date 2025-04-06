```
ssh_key_pass() :: String
```

Die Funktion `ssh_key_pass()` gibt den Wert der Umgebungsvariable `SSH_KEY_PASS` zurück, wenn sie gesetzt ist, oder `nothing`, wenn sie nicht gesetzt ist. In Zukunft könnte es möglich sein, ein Passwort auf andere Weise zu finden, wie z.B. durch sicheren Systemspeicher. Daher sollten Pakete, die ein Passwort zum Entschlüsseln eines SSH-Privatschlüssels benötigen, diese API verwenden, anstatt direkt die Umgebungsvariable zu überprüfen, damit sie solche Fähigkeiten automatisch erhalten, wenn sie hinzugefügt werden.
