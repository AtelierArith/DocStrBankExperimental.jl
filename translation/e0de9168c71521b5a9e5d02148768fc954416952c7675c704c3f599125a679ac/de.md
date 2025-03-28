```
empty(a::AbstractDict, [index_type=keytype(a)], [value_type=valtype(a)])
```

Erstellt einen leeren `AbstractDict`-Container, der Indizes vom Typ `index_type` und Werte vom Typ `value_type` akzeptieren kann. Die zweiten und dritten Argumente sind optional und standardmäßig auf den `keytype` und `valtype` des Eingangs gesetzt. (Wenn nur einer der beiden Typen angegeben ist, wird angenommen, dass es sich um den `value_type` handelt, und der `index_type` wird standardmäßig auf `keytype(a)` gesetzt).

Benutzerdefinierte `AbstractDict`-Subtypen können wählen, welcher spezifische Dictionary-Typ am besten für die gegebenen Index- und Werttypen geeignet ist, indem sie sich auf die dre argumentige Signatur spezialisieren. Der Standardwert ist, ein leeres `Dict` zurückzugeben.
