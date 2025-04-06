```
print([io::IO = stdout,] [data::Vector = fetch()], [lidict::Union{LineInfoDict, LineInfoFlatDict} = getdict(data)]; kwargs...)
```

Gibt Profiling-Ergebnisse an `io` aus (standardmäßig `stdout`). Wenn Sie keinen `data`-Vektor angeben, wird der interne Puffer von angesammelten Backtraces verwendet.

Die Schlüsselwortargumente können eine beliebige Kombination aus folgenden sein:

  * `format` – Bestimmt, ob Backtraces mit (Standard, `:tree`) oder ohne (`:flat`) Einrückung, die die Baumstruktur anzeigt, ausgegeben werden.
  * `C` – Wenn `true`, werden Backtraces aus C- und Fortran-Code angezeigt (normalerweise werden sie ausgeschlossen).
  * `combine` – Wenn `true` (Standard), werden die Befehlszeiger zusammengeführt, die der gleichen Codezeile entsprechen.
  * `maxdepth` – Begrenzung der Tiefe über `maxdepth` im `:tree`-Format.
  * `sortedby` – Steuert die Reihenfolge im `:flat`-Format. `:filefuncline` (Standard) sortiert nach der Quellzeile, `:count` sortiert in der Reihenfolge der Anzahl gesammelter Proben, und `:overhead` sortiert nach der Anzahl der Proben, die jede Funktion für sich selbst verursacht hat.
  * `groupby` – Steuert die Gruppierung über Aufgaben und Threads oder keine Gruppierung. Optionen sind `:none` (Standard), `:thread`, `:task`, `[:thread, :task]` oder `[:task, :thread]`, wobei die letzten beiden eine geschachtelte Gruppierung bieten.
  * `noisefloor` – Begrenzung von Frames, die den heuristischen Geräuschpegel der Probe überschreiten (gilt nur für das Format `:tree`). Ein empfohlener Wert, den Sie ausprobieren können, ist 2.0 (der Standardwert ist 0). Dieses Parameter verbirgt Proben, für die `n <= noisefloor * √N`, wobei `n` die Anzahl der Proben in dieser Zeile und `N` die Anzahl der Proben für den Aufrufer ist.
  * `mincount` – Begrenzung der Ausgabe auf nur die Zeilen mit mindestens `mincount` Vorkommen.
  * `recur` – Steuert die Handhabung der Rekursion im `:tree`-Format. `:off` (Standard) gibt den Baum normal aus. `:flat` hingegen komprimiert jede Rekursion (nach ip) und zeigt die ungefähren Auswirkungen der Umwandlung jeder Selbstrekursion in einen Iterator. `:flatc` macht dasselbe, schließt jedoch auch das Zusammenfassen von C-Frames ein (kann seltsame Dinge um `jl_apply` herum tun).
  * `threads::Union{Int,AbstractVector{Int}}` – Geben Sie an, von welchen Threads Schnappschüsse im Bericht enthalten sein sollen. Beachten Sie, dass dies nicht steuert, von welchen Threads Proben gesammelt werden (die möglicherweise auch auf einem anderen Computer gesammelt wurden).
  * `tasks::Union{Int,AbstractVector{Int}}` – Geben Sie an, von welchen Aufgaben Schnappschüsse im Bericht enthalten sein sollen. Beachten Sie, dass dies nicht steuert, innerhalb welcher Aufgaben Proben gesammelt werden.

!!! compat "Julia 1.8"
    Die Schlüsselwortargumente `groupby`, `threads` und `tasks` wurden in Julia 1.8 eingeführt.


!!! note
    Profiling unter Windows ist auf den Hauptthread beschränkt. Andere Threads wurden nicht beprobt und werden im Bericht nicht angezeigt.

