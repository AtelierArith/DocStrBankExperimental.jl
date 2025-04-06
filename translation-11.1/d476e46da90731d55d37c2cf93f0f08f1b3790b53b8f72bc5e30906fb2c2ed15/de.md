```
Base.runtests(tests=["all"]; ncores=ceil(Int, Sys.CPU_THREADS / 2),
              exit_on_error=false, revise=false, [seed])
```

Führen Sie die in `tests` aufgeführten Julia-Einheitstests aus, die entweder eine Zeichenfolge oder ein Array von Zeichenfolgen sein können, unter Verwendung von `ncores` Prozessoren. Wenn `exit_on_error` auf `false` gesetzt ist, werden bei einem fehlgeschlagenen Test alle verbleibenden Tests in anderen Dateien weiterhin ausgeführt; andernfalls werden sie verworfen, wenn `exit_on_error == true`. Wenn `revise` auf `true` gesetzt ist, wird das `Revise`-Paket verwendet, um alle Änderungen an `Base` oder an den Standardbibliotheken vor der Ausführung der Tests zu laden. Wenn ein Seed über das Schlüsselwort-Argument bereitgestellt wird, wird er verwendet, um den globalen RNG im Kontext, in dem die Tests ausgeführt werden, zu initialisieren; andernfalls wird der Seed zufällig gewählt.
