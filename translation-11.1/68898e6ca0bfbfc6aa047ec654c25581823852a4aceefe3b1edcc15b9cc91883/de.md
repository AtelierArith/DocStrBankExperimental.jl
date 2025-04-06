```
message(c::GitCommit, raw::Bool=false)
```

Gibt die Commit-Nachricht zurück, die die in Commit `c` vorgenommenen Änderungen beschreibt. Wenn `raw` `false` ist, wird eine leicht "bereinigte" Nachricht zurückgegeben (die alle führenden Zeilenumbrüche entfernt hat). Wenn `raw` `true` ist, wird die Nachricht nicht von solchen Zeilenumbrüchen befreit.
