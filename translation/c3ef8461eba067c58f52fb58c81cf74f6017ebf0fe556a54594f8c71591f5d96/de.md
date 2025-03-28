```
fetch(repo::GitRepo; kwargs...)
```

Holt Updates von einem Upstream des Repositories `repo`.

Die Schlüsselwortargumente sind:

  * `remote::AbstractString="origin"`: welcher Remote, angegeben durch den Namen, von `repo` abgerufen werden soll. Wenn dies leer ist, wird die URL verwendet, um einen anonymen Remote zu erstellen.
  * `remoteurl::AbstractString=""`: die URL von `remote`. Wenn nicht angegeben, wird sie basierend auf dem gegebenen Namen von `remote` angenommen.
  * `refspecs=AbstractString[]`: bestimmt die Eigenschaften des Abrufs.
  * `credentials=nothing`: bietet Anmeldeinformationen und/oder Einstellungen beim Authentifizieren gegen einen privaten `remote`.
  * `callbacks=Callbacks()`: vom Benutzer bereitgestellte Rückrufe und Payloads.

Entspricht `git fetch [<remoteurl>|<repo>] [<refspecs>]`.
