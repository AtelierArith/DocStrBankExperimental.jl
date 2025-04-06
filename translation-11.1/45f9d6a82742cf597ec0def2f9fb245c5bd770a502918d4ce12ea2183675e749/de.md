```
push(rmt::GitRemote, refspecs; force::Bool=false, options::PushOptions=PushOptions())
```

Pushen Sie in das angegebene `rmt` Remote-Git-Repository, wobei `refspecs` verwendet wird, um zu bestimmen, in welchen Remote-Branch(es) gepusht werden soll. Die Schlüsselwortargumente sind:

  * `force`: wenn `true`, wird ein Force-Push durchgeführt, der Konflikte ignoriert.
  * `options`: bestimmt die Optionen für den Push, z. B. welche Proxy-Header verwendet werden sollen. Siehe [`PushOptions`](@ref) für weitere Informationen.

!!! note
    Sie können Informationen über die Push-Refspecs auf zwei andere Arten hinzufügen: indem Sie eine Option in der `GitConfig` des Repositories festlegen (mit `push.default` als Schlüssel) oder indem Sie [`add_push!`](@ref) aufrufen. Andernfalls müssen Sie eine Push-Refspec explizit im Aufruf von `push` angeben, damit sie Wirkung zeigt, wie folgt: `LibGit2.push(repo, refspecs=["refs/heads/master"])`.

