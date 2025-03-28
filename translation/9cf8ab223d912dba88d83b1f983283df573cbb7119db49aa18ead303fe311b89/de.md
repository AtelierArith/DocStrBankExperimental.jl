```
@test_logs [log_patterns...] [keywords] Ausdruck
```

Sammeln Sie eine Liste von Protokolleinträgen, die durch `Ausdruck` generiert werden, indem Sie `collect_test_logs` verwenden, überprüfen Sie, ob sie mit der Sequenz `log_patterns` übereinstimmen, und geben Sie den Wert von `Ausdruck` zurück. Die `keywords` bieten eine einfache Filterung der Protokolleinträge: das `min_level`-Keyword steuert das minimale Protokollniveau, das für den Test gesammelt wird, das `match_mode`-Keyword definiert, wie das Matching durchgeführt wird (das Standard-`:all` überprüft, ob alle Protokolle und Muster paarweise übereinstimmen; verwenden Sie `:any`, um zu überprüfen, ob das Muster irgendwo in der Sequenz mindestens einmal übereinstimmt.)

Das nützlichste Protokollmuster ist ein einfaches Tupel der Form `(level,message)`. Eine andere Anzahl von Tupel-Elementen kann verwendet werden, um andere Protokollmetadaten abzugleichen, die den Argumenten entsprechen, die an `AbstractLogger` über die Funktion `handle_message` übergeben werden: `(level,message,module,group,id,file,line)`. Elemente, die vorhanden sind, werden standardmäßig paarweise mit den Feldern des Protokolleintrags unter Verwendung von `==` abgeglichen, wobei die Sonderfälle, dass `Symbol`s für die Standardprotokollniveaus verwendet werden können, und `Regex`s im Muster die String- oder Symbolfelder mit `occursin` abgleichen.

# Beispiele

Betrachten Sie eine Funktion, die eine Warnung protokolliert und mehrere Debug-Nachrichten:

```
function foo(n)
    @info "Doing foo with n=$n"
    for i=1:n
        @debug "Iteration $i"
    end
    42
end
```

Wir können die Info-Nachricht testen mit

```
@test_logs (:info,"Doing foo with n=2") foo(2)
```

Wenn wir auch die Debug-Nachrichten testen möchten, müssen diese mit dem `min_level`-Keyword aktiviert werden:

```
using Logging
@test_logs (:info,"Doing foo with n=2") (:debug,"Iteration 1") (:debug,"Iteration 2") min_level=Logging.Debug foo(2)
```

Wenn Sie testen möchten, dass bestimmte Nachrichten generiert werden, während der Rest ignoriert wird, können Sie das Keyword `match_mode=:any` setzen:

```
using Logging
@test_logs (:info,) (:debug,"Iteration 42") min_level=Logging.Debug match_mode=:any foo(100)
```

Das Makro kann mit `@test` verkettet werden, um auch den zurückgegebenen Wert zu testen:

```
@test (@test_logs (:info,"Doing foo with n=2") foo(2)) == 42
```

Wenn Sie auf das Fehlen von Warnungen testen möchten, können Sie die Angabe von Protokollmustern weglassen und das `min_level` entsprechend setzen:

```
# testen, dass der Ausdruck keine Nachrichten protokolliert, wenn das Logger-Niveau warn ist:
@test_logs min_level=Logging.Warn @info("Some information") # besteht
@test_logs min_level=Logging.Warn @warn("Some information") # schlägt fehl
```

Wenn Sie das Fehlen von Warnungen (oder Fehlermeldungen) in [`stderr`](@ref) testen möchten, die nicht durch `@warn` generiert werden, siehe [`@test_nowarn`](@ref). ```
