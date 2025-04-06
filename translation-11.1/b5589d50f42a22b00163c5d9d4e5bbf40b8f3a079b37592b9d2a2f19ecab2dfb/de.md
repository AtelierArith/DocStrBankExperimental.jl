```
dlsym(handle, sym; throw_error::Bool = true)
```

Sucht ein Symbol aus einem Shared-Library-Handle und gibt einen aufrufbaren Funktionszeiger im Erfolgsfall zurück.

Wenn das Symbol nicht gefunden werden kann, wirft diese Methode einen Fehler, es sei denn, das Schlüsselwortargument `throw_error` ist auf `false` gesetzt, in diesem Fall gibt diese Methode `nothing` zurück.
