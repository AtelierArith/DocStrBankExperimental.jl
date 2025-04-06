```
versioninfo(io::IO=stdout; verbose::Bool=false)
```

Gibt Informationen über die verwendete Version von Julia aus. Die Ausgabe wird mit booleschen Schlüsselwortargumenten gesteuert:

  * `verbose`: alle zusätzlichen Informationen ausgeben

!!! warning
    Die Ausgabe dieser Funktion kann sensible Informationen enthalten. Überprüfen Sie die Ausgabe, bevor Sie sie teilen, und entfernen Sie alle Daten, die nicht öffentlich geteilt werden sollten.


Siehe auch: [`VERSION`](@ref).
