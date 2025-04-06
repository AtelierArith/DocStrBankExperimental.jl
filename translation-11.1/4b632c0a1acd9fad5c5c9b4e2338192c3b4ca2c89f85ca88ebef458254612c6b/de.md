```
@distributed
```

Eine verteilte Speicher-, parallele Schleife der Form:

```
@distributed [reducer] for var = range
    body
end
```

Der angegebene Bereich wird partitioniert und lokal über alle Arbeiter ausgeführt. Falls eine optionale Reduzierfunktion angegeben ist, führt `@distributed` lokale Reduzierungen auf jedem Arbeiter durch, gefolgt von einer endgültigen Reduzierung im aufrufenden Prozess.

Beachten Sie, dass `@distributed` ohne eine Reduzierfunktion asynchron ausgeführt wird, d.h. es startet unabhängige Aufgaben auf allen verfügbaren Arbeitern und gibt sofort zurück, ohne auf den Abschluss zu warten. Um auf den Abschluss zu warten, setzen Sie den Aufruf mit [`@sync`](@ref) in der Form:

```
@sync @distributed for var = range
    body
end
```
