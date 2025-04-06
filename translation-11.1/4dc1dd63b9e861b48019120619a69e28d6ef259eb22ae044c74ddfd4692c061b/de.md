```
remotecall(f, id::Integer, args...; kwargs...) -> Future
```

Rufe eine Funktion `f` asynchron mit den angegebenen Argumenten auf dem angegebenen Prozess auf. Gibt ein [`Future`](@ref) zurück. Schlüsselwortargumente, falls vorhanden, werden an `f` weitergegeben.
