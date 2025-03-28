```
open(filename::AbstractString; lock = true, keywords...) -> IOStream
```

Öffnen Sie eine Datei in einem Modus, der durch fünf boolesche Schlüsselwortargumente angegeben ist:

| Schlüsselwort | Beschreibung                    | Standard                              |
|:------------- |:------------------------------- |:------------------------------------- |
| `read`        | zum Lesen öffnen                | `!write`                              |
| `write`       | zum Schreiben öffnen            | `truncate \| append`                  |
| `create`      | erstellen, wenn nicht vorhanden | `!read & write \| truncate \| append` |
| `truncate`    | auf null Größe kürzen           | `!read & write`                       |
| `append`      | zum Ende suchen                 | `false`                               |

Der Standardwert, wenn keine Schlüsselwörter übergeben werden, ist, Dateien nur zum Lesen zu öffnen. Gibt einen Stream zum Zugreifen auf die geöffnete Datei zurück.

Das Schlüsselwortargument `lock` steuert, ob Operationen für einen sicheren mehrstufigen Zugriff gesperrt werden.

!!! compat "Julia 1.5"
    Das Argument `lock` ist seit Julia 1.5 verfügbar.

