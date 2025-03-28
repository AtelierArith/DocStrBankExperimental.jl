```
arg_mkdir(f::Function, arg::AbstractString) -> arg
arg_mkdir(f::Function, arg::Nothing) -> mktempdir()
```

Die Funktion `arg_mkdir` nimmt `arg`, das entweder eines der folgenden sein muss:

  * ein Pfad zu einem bereits vorhandenen leeren Verzeichnis,
  * ein nicht vorhandener Pfad, der als Verzeichnis erstellt werden kann, oder
  * `nothing`, in diesem Fall wird ein temporäres Verzeichnis erstellt.

In allen Fällen wird der Pfad zum Verzeichnis zurückgegeben. Wenn ein Fehler während `f(arg)` auftritt, wird das Verzeichnis in seinen ursprünglichen Zustand zurückversetzt: Wenn es bereits existierte, aber leer war, wird es geleert; wenn es nicht existierte, wird es gelöscht.
