```
isbinary(blob::GitBlob) -> Bool
```

Utiliza una heurística para adivinar si un archivo es binario: buscando bytes NULL y buscando una relación razonable de caracteres imprimibles a no imprimibles entre los primeros 8000 bytes.
