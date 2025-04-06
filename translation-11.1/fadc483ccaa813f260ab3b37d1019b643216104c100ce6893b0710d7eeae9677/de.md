```
task_local_storage(body, key, value)
```

Rufen Sie die Funktion `body` mit einem modifizierten aufgabenlokalen Speicher auf, in dem `value` `key` zugewiesen wird; der vorherige Wert von `key` oder dessen Fehlen wird danach wiederhergestellt. Nützlich zum Emulieren von dynamischem Scoping.
