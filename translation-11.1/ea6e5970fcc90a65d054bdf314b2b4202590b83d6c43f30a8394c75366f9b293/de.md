```
reenable_sigint(f::Function)
```

Reaktiviert den Ctrl-C-Handler während der Ausführung einer Funktion. Kehrt vorübergehend die Wirkung von [`disable_sigint`](@ref) um.
