```
push(repo::GitRepo; kwargs...)
```

Überträgt Updates an ein Upstream von `repo`.

Die Schlüsselwortargumente sind:

  * `remote::AbstractString="origin"`: der Name des Upstream-Remotes, zu dem übertragen werden soll.
  * `remoteurl::AbstractString=""`: die URL von `remote`.
  * `refspecs=AbstractString[]`: bestimmt die Eigenschaften des Pushs.
  * `force::Bool=false`: bestimmt, ob der Push ein Force-Push sein wird, der den Remote-Zweig überschreibt.
  * `credentials=nothing`: stellt Anmeldeinformationen und/oder Einstellungen zur Verfügung, wenn gegen ein privates `remote` authentifiziert wird.
  * `callbacks=Callbacks()`: vom Benutzer bereitgestellte Rückrufe und Payloads.

Entspricht `git push [<remoteurl>|<repo>] [<refspecs>]`.
