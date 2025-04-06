```
clear_malloc_data()
```

Löscht alle gespeicherten Speicherzuweisungsdaten, wenn Julia mit `--track-allocation` ausgeführt wird. Führen Sie die Befehle aus, die Sie testen möchten (um die JIT-Kompilierung zu erzwingen), und rufen Sie dann [`clear_malloc_data`](@ref) auf. Führen Sie dann Ihre Befehle erneut aus, beenden Sie Julia und überprüfen Sie die resultierenden `*.mem`-Dateien.
