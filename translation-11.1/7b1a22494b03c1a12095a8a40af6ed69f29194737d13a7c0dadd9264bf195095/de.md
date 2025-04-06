```
LogLevel(level)
```

Schweregrad/Detailgenauigkeit eines Protokolleintrags.

Das Protokollniveau bietet einen Schlüssel, anhand dessen potenzielle Protokolleinträge gefiltert werden können, bevor weitere Arbeiten zur Konstruktion der Protokolleintragsdatenstruktur selbst durchgeführt werden.

# Beispiele

```julia-repl
julia> Logging.LogLevel(0) == Logging.Info
true
```
