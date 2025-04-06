```
LAPACKException
```

Allgemeine LAPACK-Ausnahme, die entweder während direkter Aufrufe der [LAPACK-Funktionen](@ref man-linalg-lapack-functions) oder während Aufrufen anderer Funktionen, die die LAPACK-Funktionen intern verwenden, aber keine spezialisierte Fehlerbehandlung haben, ausgelöst wird. Das Feld `info` enthält zusätzliche Informationen über den zugrunde liegenden Fehler und hängt von der aufgerufenen LAPACK-Funktion ab.
