```
isbinary(blob::GitBlob) -> Bool
```

Verwenden Sie eine Heuristik, um zu erraten, ob eine Datei binär ist: Suchen nach NULL-Bytes und Überprüfen eines angemessenen Verhältnisses von druckbaren zu nicht druckbaren Zeichen in den ersten 8000 Bytes.
