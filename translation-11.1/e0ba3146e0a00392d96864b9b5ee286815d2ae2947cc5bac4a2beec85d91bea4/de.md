```
diff_files(repo::GitRepo, branch1::AbstractString, branch2::AbstractString; kwarg...) -> Vector{AbstractString}
```

Zeigt an, welche Dateien im Git-Repository `repo` zwischen den Branches `branch1` und `branch2` geändert wurden.

Das Schlüsselwort-Argument ist:

  * `filter::Set{Consts.DELTA_STATUS}=Set([Consts.DELTA_ADDED, Consts.DELTA_MODIFIED, Consts.DELTA_DELETED]))`, und es legt Optionen für den Diff fest. Der Standardwert zeigt hinzugefügte, geänderte oder gelöschte Dateien an.

Gibt nur die *Namen* der Dateien zurück, die sich geändert haben, *nicht* deren Inhalte.

# Beispiele

```julia
LibGit2.branch!(repo, "branch/a")
LibGit2.branch!(repo, "branch/b")
# füge eine Datei zum Repo hinzu
open(joinpath(LibGit2.path(repo),"file"),"w") do f
    write(f, "hello repo
")
end
LibGit2.add!(repo, "file")
LibGit2.commit(repo, "add file")
# gibt ["file"] zurück
filt = Set([LibGit2.Consts.DELTA_ADDED])
files = LibGit2.diff_files(repo, "branch/a", "branch/b", filter=filt)
# gibt [] zurück, weil bestehende Dateien nicht geändert wurden
filt = Set([LibGit2.Consts.DELTA_MODIFIED])
files = LibGit2.diff_files(repo, "branch/a", "branch/b", filter=filt)
```

Entspricht `git diff --name-only --diff-filter=<filter> <branch1> <branch2>`.
