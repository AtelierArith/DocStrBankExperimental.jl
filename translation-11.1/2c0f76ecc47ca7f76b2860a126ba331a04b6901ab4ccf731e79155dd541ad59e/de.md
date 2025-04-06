```
LibGit2.tag_create(repo::GitRepo, tag::AbstractString, commit; kwargs...)
```

Erstellt ein neues Git-Tag `tag` (z. B. `"v0.5"`) im Repository `repo`, beim Commit `commit`.

Die Schlüsselwortargumente sind:

  * `msg::AbstractString=""`: die Nachricht für das Tag.
  * `force::Bool=false`: wenn `true`, werden vorhandene Referenzen überschrieben.
  * `sig::Signature=Signature(repo)`: die Signatur des Taggers.
