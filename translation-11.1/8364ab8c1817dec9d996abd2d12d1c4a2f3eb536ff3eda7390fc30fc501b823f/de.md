```
fdio([name::AbstractString, ]fd::Integer[, own::Bool=false]) -> IOStream
```

Erstellt ein [`IOStream`](@ref) Objekt aus einem ganzzahligen Dateideskriptor. Wenn `own` `true` ist, wird das Schließen dieses Objekts den zugrunde liegenden Deskriptor schließen. Standardmäßig wird ein `IOStream` geschlossen, wenn er garbage collected wird. `name` ermöglicht es Ihnen, den Deskriptor mit einer benannten Datei zu verknüpfen.
