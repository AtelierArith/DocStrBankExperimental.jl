```
strptime([format], timestr)
```

Analysiere einen formatierten Zeitstring in eine `TmStruct`, die die Sekunden, Minuten, Stunden, das Datum usw. angibt. Unterstützte Formate sind die gleichen wie die in der Standard-C-Bibliothek. Auf einigen Plattformen werden Zeitzonen möglicherweise nicht korrekt analysiert. Wenn das Ergebnis dieser Funktion an `time` übergeben wird, um es in Sekunden seit der Epoche zu konvertieren, sollte das Feld `isdst` manuell ausgefüllt werden. Es auf `-1` zu setzen, teilt der C-Bibliothek mit, die aktuellen Systemeinstellungen zur Bestimmung der Zeitzone zu verwenden.
