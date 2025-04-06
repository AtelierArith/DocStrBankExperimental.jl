```
LibGit2.tag_create(repo::GitRepo, tag::AbstractString, commit; kwargs...)
```

Yeni bir git etiketi `tag` (örneğin, `"v0.5"`) oluşturur, `repo` deposunda, `commit` üzerinde.

Anahtar kelime argümanları şunlardır:

  * `msg::AbstractString=""`: etiket için mesaj.
  * `force::Bool=false`: `true` ise, mevcut referanslar üzerine yazılacaktır.
  * `sig::Signature=Signature(repo)`: etiketleyicinin imzası.
