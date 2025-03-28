```
fetch(;include_meta = true) -> data
```

Gibt eine Kopie des Puffers von Profil-Backtraces zurück. Beachten Sie, dass die Werte in `data` nur auf dieser Maschine in der aktuellen Sitzung Bedeutung haben, da sie von den genauen Speicheradressen abhängen, die beim JIT-Kompilieren verwendet werden. Diese Funktion ist hauptsächlich für den internen Gebrauch; [`retrieve`](@ref) könnte für die meisten Benutzer eine bessere Wahl sein. Standardmäßig sind Metadaten wie threadid und taskid enthalten. Setzen Sie `include_meta` auf `false`, um Metadaten zu entfernen.
