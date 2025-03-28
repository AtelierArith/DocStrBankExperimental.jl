```
Profile.Allocs.print([io::IO = stdout,] [data::AllocResults = fetch()]; kwargs...)
```

Gibt die Profilierungsergebnisse an `io` aus (standardmäßig `stdout`). Wenn Sie keinen `data`-Vektor angeben, wird der interne Puffer der angesammelten Backtraces verwendet.

Siehe `Profile.print` für eine Erklärung der gültigen Schlüsselwortargumente.
