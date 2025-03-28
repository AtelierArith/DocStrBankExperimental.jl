```
free(addr::Ptr)
```

Rufen Sie `free` aus der C-Standardbibliothek auf. Verwenden Sie dies nur für Speicher, der von [`malloc`](@ref) erhalten wurde, nicht für Zeiger, die aus anderen C-Bibliotheken abgerufen wurden. [`Ptr`](@ref)-Objekte, die aus C-Bibliotheken erhalten wurden, sollten mit den in dieser Bibliothek definierten Freifunktionen freigegeben werden, um Assertion-Fehler zu vermeiden, wenn mehrere `libc`-Bibliotheken im System vorhanden sind.
