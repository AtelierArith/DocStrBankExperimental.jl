```
ssh_known_hosts_file() :: String
```

Die Funktion `ssh_known_hosts_file()` gibt einen einzelnen Pfad zu einer SSH-known-hosts-Datei zurück, die verwendet werden sollte, wenn die Identitäten von Remote-Servern für SSH-Verbindungen festgestellt werden. Sie gibt den ersten Pfad zurück, der von `ssh_known_hosts_files` zurückgegeben wird und tatsächlich existiert. Aufrufer, die in mehr als einer known-hosts-Datei nachsehen können, sollten stattdessen `ssh_known_hosts_files` verwenden und nach Hostübereinstimmungen in allen Dateien suchen, die in den Dokumentationen dieser Funktion beschrieben sind.
