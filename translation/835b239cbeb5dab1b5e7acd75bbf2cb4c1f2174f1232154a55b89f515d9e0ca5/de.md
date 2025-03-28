```
exit_on_sigint(on::Bool)
```

Setze das `exit_on_sigint`-Flag der Julia-Laufzeit. Wenn `false`, kann Ctrl-C (SIGINT) als [`InterruptException`](@ref) im `try`-Block erfasst werden. Dies ist das Standardverhalten im REPL, bei jedem Code, der über `-e` und `-E` ausgeführt wird, und in Julia-Skripten, die mit der `-i`-Option ausgeführt werden.

Wenn `true`, wird `InterruptException` nicht durch Ctrl-C ausgelöst. Das Ausführen von Code bei einem solchen Ereignis erfordert [`atexit`](@ref). Dies ist das Standardverhalten in Julia-Skripten, die ohne die `-i`-Option ausgeführt werden.

!!! compat "Julia 1.5"
    Die Funktion `exit_on_sigint` erfordert mindestens Julia 1.5.

