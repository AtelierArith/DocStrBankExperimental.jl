```
print([io::IO = stdout,] data::Vector, lidict::LineInfoDict; kwargs...)
```

Gibt die Profilierungsergebnisse an `io` aus. Diese Variante wird verwendet, um Ergebnisse zu untersuchen, die von einem vorherigen Aufruf von [`retrieve`](@ref) exportiert wurden. Übergeben Sie den Vektor `data` von Backtraces und ein Wörterbuch `lidict` mit Zeileninformationen.

Siehe `Profile.print([io], data)` für eine Erklärung der gültigen Schlüsselwortargumente.
