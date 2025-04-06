```
Base.checked_length(r)
```

Berechnet `length(r)`, prüft jedoch möglicherweise auf Überlauf-Fehler, wo anwendbar, wenn das Ergebnis nicht in `Union{Integer(eltype(r)),Int}` passt.
