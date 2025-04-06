```
addprocs(manager::ClusterManager; kwargs...) -> Liste der Prozessidentifikatoren
```

Startet Arbeitsprozesse über den angegebenen Cluster-Manager.

Zum Beispiel werden Beowulf-Cluster über einen benutzerdefinierten Cluster-Manager unterstützt, der im Paket `ClusterManagers.jl` implementiert ist.

Die Anzahl der Sekunden, die ein neu gestarteter Arbeiter auf die Verbindungsherstellung vom Master wartet, kann über die Variable `JULIA_WORKER_TIMEOUT` in der Umgebung des Arbeiterprozesses angegeben werden. Relevant nur bei Verwendung von TCP/IP als Transport.

Um Arbeiter zu starten, ohne die REPL oder die umgebende Funktion zu blockieren, wenn Arbeiter programmgesteuert gestartet werden, führen Sie `addprocs` in seiner eigenen Aufgabe aus.

# Beispiele

```julia
# In beschäftigten Clustern `addprocs` asynchron aufrufen
t = @async addprocs(...)
```

```julia
# Arbeiter nutzen, sobald sie online sind
if nprocs() > 1   # Sicherstellen, dass mindestens ein neuer Arbeiter verfügbar ist
   ....   # verteilte Ausführung durchführen
end
```

```julia
# Neu gestartete Arbeiter-IDs oder Fehlermeldungen abrufen
if istaskdone(t)   # Überprüfen, ob `addprocs` abgeschlossen ist, um sicherzustellen, dass `fetch` nicht blockiert
    if nworkers() == N
        new_pids = fetch(t)
    else
        fetch(t)
    end
end
```
