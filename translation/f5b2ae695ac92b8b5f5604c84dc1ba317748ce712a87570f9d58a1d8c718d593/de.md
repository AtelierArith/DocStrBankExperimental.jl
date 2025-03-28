```
disable_sigint(f::Function)
```

Deaktiviert den Ctrl-C-Handler während der Ausführung einer Funktion im aktuellen Task, um externen Code aufzurufen, der möglicherweise Julia-Code aufruft, der nicht unterbrechungssicher ist. Soll mit der `do`-Block-Syntax wie folgt aufgerufen werden:

```
disable_sigint() do
    # unterbrechungsunsicherer Code
    ...
end
```

Dies ist in Arbeitsthreads (`Threads.threadid() != 1`) nicht erforderlich, da die `InterruptException` nur an den Master-Thread gesendet wird. Externe Funktionen, die keinen Julia-Code oder die Julia-Laufzeit aufrufen, deaktivieren automatisch sigint während ihrer Ausführung.
