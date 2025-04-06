```
pipeline(command; stdin, stdout, stderr, append=false)
```

Leitet I/O zu oder von dem angegebenen `command` um. Schlüsselwortargumente geben an, welche der Streams des Befehls umgeleitet werden sollen. `append` steuert, ob die Dateiausgabe an die Datei angehängt wird. Dies ist eine allgemeinere Version der 2-Argumente `pipeline`-Funktion. `pipeline(from, to)` ist äquivalent zu `pipeline(from, stdout=to)`, wenn `from` ein Befehl ist, und zu `pipeline(to, stdin=from)`, wenn `from` eine andere Art von Datenquelle ist.

**Beispiele**:

```julia
run(pipeline(`dothings`, stdout="out.txt", stderr="errs.txt"))
run(pipeline(`update`, stdout="log.txt", append=true))
```
