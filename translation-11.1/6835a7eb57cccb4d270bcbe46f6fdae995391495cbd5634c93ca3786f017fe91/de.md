```
link_pipe!(pipe; reader_supports_async=false, writer_supports_async=false)
```

Initialisiere `pipe` und verlinke den `in` Endpunkt mit dem `out` Endpunkt. Die Schlüsselwortargumente `reader_supports_async`/`writer_supports_async` entsprechen `OVERLAPPED` unter Windows und `O_NONBLOCK` unter POSIX-Systemen. Sie sollten `true` sein, es sei denn, sie werden von einem externen Programm verwendet (z. B. die Ausgabe eines mit [`run`](@ref) ausgeführten Befehls).
