```
LibGit2.tag_create(repo::GitRepo, tag::AbstractString, commit; kwargs...)
```

Créez un nouveau tag git `tag` (par exemple, `"v0.5"`) dans le dépôt `repo`, au commit `commit`.

Les arguments de mot-clé sont :

  * `msg::AbstractString=""`: le message pour le tag.
  * `force::Bool=false`: si `true`, les références existantes seront écrasées.
  * `sig::Signature=Signature(repo)`: la signature du tagueur.
