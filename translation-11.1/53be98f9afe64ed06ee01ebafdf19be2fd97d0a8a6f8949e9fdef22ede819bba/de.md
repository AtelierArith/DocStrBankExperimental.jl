```
reset(::Event)
```

Setzt ein [`Event`](@ref) zurück in einen nicht gesetzten Zustand. Zukünftige Aufrufe von `wait` blockieren dann, bis [`notify`](@ref) erneut aufgerufen wird.
