```
reset!(repo::GitRepo, id::GitHash, mode::Cint=Consts.RESET_MIXED)
```

Setze das Repository `repo` auf seinen Zustand bei `id` zurück, wobei einer der drei Modi verwendet wird, die durch `mode` festgelegt sind:

1. `Consts.RESET_SOFT` - bewege HEAD zu `id`.
2. `Consts.RESET_MIXED` - Standard, bewege HEAD zu `id` und setze den Index auf `id` zurück.
3. `Consts.RESET_HARD` - bewege HEAD zu `id`, setze den Index auf `id` zurück und verwerfe alle Änderungen im Arbeitsverzeichnis.

# Beispiele

```julia
# Änderungen abrufen
LibGit2.fetch(repo)
isfile(joinpath(repo_path, our_file)) # wird false sein

# Änderungen mit Fast-Forward zusammenführen
LibGit2.merge!(repo, fastforward=true)

# Da es lokal keine Datei gab, aber es eine
# Datei remote gibt, müssen wir den Branch zurücksetzen
head_oid = LibGit2.head_oid(repo)
new_head = LibGit2.reset!(repo, head_oid, LibGit2.Consts.RESET_HARD)
```

In diesem Beispiel hat das Remote, von dem abgerufen wird, *eine* Datei namens `our_file` in seinem Index, weshalb wir zurücksetzen müssen.

Entspricht `git reset [--soft | --mixed | --hard] <id>`.

# Beispiele

```julia
repo = LibGit2.GitRepo(repo_path)
head_oid = LibGit2.head_oid(repo)
open(joinpath(repo_path, "file1"), "w") do f
    write(f, "111
")
end
LibGit2.add!(repo, "file1")
mode = LibGit2.Consts.RESET_HARD
# wird die Änderungen an file1 verwerfen
# und es unstagen
new_head = LibGit2.reset!(repo, head_oid, mode)
```
