```
ssh_known_hosts_files() :: Vector{String}
```

Die Funktion `ssh_known_hosts_files()` gibt einen Vektor von Pfaden zu SSH bekannten Hosts-Dateien zurück, die verwendet werden sollten, wenn die Identitäten von Remote-Servern für SSH-Verbindungen hergestellt werden. Standardmäßig gibt diese Funktion zurück

```
[joinpath(ssh_dir(), "known_hosts"), bundled_known_hosts]
```

wobei `bundled_known_hosts` der Pfad zu einer Kopie einer bekannten Hosts-Datei ist, die mit diesem Paket gebündelt ist (enthält bekannte Hosts-Schlüssel für `github.com` und `gitlab.com`). Wenn die Umgebungsvariable `SSH_KNOWN_HOSTS_FILES` gesetzt ist, wird ihr Wert jedoch in Pfade am `:`-Zeichen (oder am `;` unter Windows) aufgeteilt und dieser Vektor von Pfaden wird stattdessen zurückgegeben. Wenn eine Komponente dieses Vektors leer ist, wird sie auf die standardmäßigen bekannten Hosts-Pfade erweitert.

Pakete, die `ssh_known_hosts_files()` verwenden, sollten idealerweise nach übereinstimmenden Einträgen suchen, indem sie den Hostnamen und die Schlüsseltypen vergleichen und den ersten Eintrag in einer der Dateien, der übereinstimmt, als die definitive Identität des Hosts betrachten. Wenn der Aufrufer den Schlüsseltyp nicht vergleichen kann (z. B. weil er gehasht wurde), muss er den obigen Algorithmus approximieren, indem er nach allen übereinstimmenden Einträgen für einen Host in jeder Datei sucht: Wenn eine Datei Einträge für einen Host hat, muss einer von ihnen übereinstimmen; der Aufrufer sollte nur dann weiter nach weiteren bekannten Hosts-Dateien suchen, wenn es in einer früheren Datei keine Einträge für den betreffenden Host gibt.
