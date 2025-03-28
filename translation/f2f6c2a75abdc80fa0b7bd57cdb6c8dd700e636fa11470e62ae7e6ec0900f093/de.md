```
callers(funcname, [data, lidict], [filename=<filename>], [linerange=<start:stop>]) -> Vector{Tuple{count, lineinfo}}
```

Geben Sie einen vorherigen Profiling-Lauf an, um zu bestimmen, wer eine bestimmte Funktion aufgerufen hat. Das Bereitstellen des Dateinamens (und optional eines Bereichs von Zeilennummern, über die die Funktion definiert ist) ermöglicht es Ihnen, eine überladene Methode zu unterscheiden. Der zurückgegebene Wert ist ein Vektor, der eine Anzahl der Aufrufe und Informationen über die Zeile des Aufrufers enthält. Man kann optional den Backtrace `data` bereitstellen, der von [`retrieve`](@ref) erhalten wurde; andernfalls wird der aktuelle interne Profilpuffer verwendet.
