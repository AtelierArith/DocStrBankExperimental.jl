```
poll_fd(fd, timeout_s::Real=-1; readable=false, writable=false)
```

Überwacht einen Dateideskriptor `fd` auf Änderungen der Lese- oder Schreibverfügbarkeit, mit einem Timeout, das durch `timeout_s` Sekunden gegeben ist.

Die Schlüsselwortargumente bestimmen, welcher Lese- und/oder Schreibstatus überwacht werden soll; mindestens eines von ihnen muss auf `true` gesetzt sein.

Der zurückgegebene Wert ist ein Objekt mit den booleschen Feldern `readable`, `writable` und `timedout`, die das Ergebnis des Pollings angeben.
