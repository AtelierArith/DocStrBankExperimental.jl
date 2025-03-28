```
ssh_key_path() :: String
```

Die Funktion `ssh_key_path()` gibt den Pfad der SSH-Privatschlüsseldatei zurück, die für SSH-Verbindungen verwendet werden sollte. Wenn die Umgebungsvariable `SSH_KEY_PATH` gesetzt ist, wird dieser Wert zurückgegeben. Andernfalls wird standardmäßig zurückgegeben

```
joinpath(ssh_dir(), ssh_key_name())
```

Dieser Standardwert hängt wiederum von den Umgebungsvariablen `SSH_DIR` und `SSH_KEY_NAME` ab.
