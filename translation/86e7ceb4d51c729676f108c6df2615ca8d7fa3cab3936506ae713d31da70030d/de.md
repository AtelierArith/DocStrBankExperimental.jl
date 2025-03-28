```
retrieve(; kwargs...) -> data, lidict
```

"Exports" Profiling-Ergebnisse in einem tragbaren Format, das die Menge aller Backtraces (`data`) und ein Wörterbuch zurückgibt, das die (sessionspezifischen) Instruktionszeiger in `data` den `LineInfo`-Werten zuordnet, die den Dateinamen, den Funktionsnamen und die Zeilennummer speichern. Diese Funktion ermöglicht es Ihnen, Profiling-Ergebnisse für zukünftige Analysen zu speichern.
