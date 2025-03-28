```
ca_roots_path() :: String
```

Die Funktion `ca_roots_path()` ist ähnlich der Funktion `ca_roots()`, mit dem Unterschied, dass sie immer einen Pfad zu einer Datei oder einem Verzeichnis von PEM-kodierten Wurzeln der Zertifizierungsstellen zurückgibt. Wenn sie auf einem System wie Windows oder macOS aufgerufen wird, wo die Systemstammzertifikate nicht im Dateisystem gespeichert sind, gibt sie derzeit den Pfad zu dem Satz von Stammzertifikaten zurück, die mit Julia gebündelt sind. (In Zukunft könnte diese Funktion stattdessen die Stammzertifikate vom System extrahieren und sie in einer Datei speichern, deren Pfad zurückgegeben wird.)

Wenn es möglich ist, eine Bibliothek, die TLS verwendet, so zu konfigurieren, dass die Systemzertifikate verwendet werden, ist das im Allgemeinen vorzuziehen: d.h. es ist besser, `ca_roots()` zu verwenden, das `nothing` zurückgibt, um anzuzeigen, dass die Systemzertifikate verwendet werden sollen. Die Funktion `ca_roots_path()` sollte nur verwendet werden, wenn Bibliotheken konfiguriert werden, die *einen* Pfad zu einer Datei oder einem Verzeichnis für Stammzertifikate *benötigen*.

Der Standardwert, der von `ca_roots_path()` zurückgegeben wird, kann überschrieben werden, indem die Umgebungsvariablen `JULIA_SSL_CA_ROOTS_PATH`, `SSL_CERT_DIR` oder `SSL_CERT_FILE` gesetzt werden, in welchem Fall diese Funktion immer den Wert der ersten dieser Variablen zurückgibt, die gesetzt ist (unabhängig davon, ob der Pfad existiert oder nicht). Wenn `JULIA_SSL_CA_ROOTS_PATH` auf den leeren String gesetzt ist, werden die anderen Variablen ignoriert (als ob sie nicht gesetzt wären); wenn die anderen Variablen auf den leeren String gesetzt sind, verhalten sie sich so, als wären sie nicht gesetzt.
