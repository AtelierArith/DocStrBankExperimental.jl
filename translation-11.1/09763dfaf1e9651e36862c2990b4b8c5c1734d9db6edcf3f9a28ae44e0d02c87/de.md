```
AsyncCondition()
```

Erstellen Sie eine asynchrone Bedingung, die Aufgaben, die darauf warten (indem sie [`wait`](@ref) auf dem Objekt aufrufen), aufweckt, wenn sie von C durch einen Aufruf von `uv_async_send` benachrichtigt werden. Wartende Aufgaben werden mit einem Fehler geweckt, wenn das Objekt geschlossen wird (durch [`close`](@ref)). Verwenden Sie [`isopen`](@ref), um zu überprüfen, ob es noch aktiv ist.

Dies bietet eine implizite Erwerbs- und Freigabereihenfolge für den Speicher zwischen den sendenden und wartenden Threads.
