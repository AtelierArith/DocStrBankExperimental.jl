```
download(url::AbstractString, [path::AbstractString = tempname()]) -> path
```

Lädt eine Datei von der angegebenen URL herunter und speichert sie am Speicherort `path`, oder, wenn nicht angegeben, an einem temporären Speicherort. Gibt den Pfad der heruntergeladenen Datei zurück.

!!! note
    Seit Julia 1.6 ist diese Funktion veraltet und ist nur ein dünner Wrapper um `Downloads.download`. In neuem Code sollten Sie diese Funktion direkt verwenden, anstatt diese aufzurufen.

