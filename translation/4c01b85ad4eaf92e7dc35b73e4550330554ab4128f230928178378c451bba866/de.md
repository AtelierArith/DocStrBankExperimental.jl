```
InterruptException()
```

Der Prozess wurde durch ein Terminal-Interrupt (CTRL+C) gestoppt.

Beachten Sie, dass in einem Julia-Skript, das ohne die Option `-i` (interaktiv) gestartet wurde, `InterruptException` standardmäßig nicht ausgelöst wird. Das Aufrufen von [`Base.exit_on_sigint(false)`](@ref Base.exit_on_sigint) im Skript kann das Verhalten der REPL wiederherstellen. Alternativ kann ein Julia-Skript mit

```sh
julia -e "include(popfirst!(ARGS))" script.jl
```

gestart werden, um zuzulassen, dass `InterruptException` während der Ausführung durch CTRL+C ausgelöst wird.
