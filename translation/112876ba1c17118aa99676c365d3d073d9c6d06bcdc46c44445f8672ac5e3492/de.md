```
ssh_pub_key_path() :: String
```

Die Funktion `ssh_pub_key_path()` gibt den Pfad der SSH-Öffentlichen Schlüsseldatei zurück, die für SSH-Verbindungen verwendet werden sollte. Wenn die Umgebungsvariable `SSH_PUB_KEY_PATH` gesetzt ist, wird dieser Wert zurückgegeben. Wenn dies nicht gesetzt ist, aber `SSH_KEY_PATH` gesetzt ist, wird dieser Pfad mit dem angehängten Suffix `.pub` zurückgegeben. Wenn keines gesetzt ist, wird standardmäßig zurückgegeben

```
joinpath(ssh_dir(), ssh_key_name() * ".pub")
```

Dieser Standardwert hängt wiederum von den Umgebungsvariablen `SSH_DIR` und `SSH_KEY_NAME` ab.
