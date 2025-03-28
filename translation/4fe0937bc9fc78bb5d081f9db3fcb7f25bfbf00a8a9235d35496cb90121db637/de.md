```
commit(repo::GitRepo, msg::AbstractString; kwargs...) -> GitHash
```

Wrapper um [`git_commit_create`](https://libgit2.org/libgit2/#HEAD/group/commit/git_commit_create). Erstelle einen Commit im Repository `repo`. `msg` ist die Commit-Nachricht. Gibt die OID des neuen Commits zurück.

Die Schlüsselwortargumente sind:

  * `refname::AbstractString=Consts.HEAD_FILE`: wenn nicht NULL, der Name der Referenz, die aktualisiert werden soll, um auf den neuen Commit zu zeigen. Zum Beispiel wird `"HEAD"` den HEAD des aktuellen Branches aktualisieren. Wenn die Referenz noch nicht existiert, wird sie erstellt.
  * `author::Signature = Signature(repo)` ist eine `Signature`, die Informationen über die Person enthält, die den Commit verfasst hat.
  * `committer::Signature = Signature(repo)` ist eine `Signature`, die Informationen über die Person enthält, die den Commit im Repository vorgenommen hat. Nicht unbedingt die gleiche wie `author`, zum Beispiel, wenn `author` einen Patch an `committer` gesendet hat, der ihn dann committed hat.
  * `tree_id::GitHash = GitHash()` ist ein Git-Baum, der verwendet wird, um den Commit zu erstellen, und zeigt seine Abstammung und Beziehung zu anderer Historie. `tree` muss zu `repo` gehören.
  * `parent_ids::Vector{GitHash}=GitHash[]` ist eine Liste von Commits von [`GitHash`](@ref), die als Eltern-Commits für den neuen verwendet werden sollen, und kann leer sein. Ein Commit kann mehrere Eltern haben, wenn es sich beispielsweise um einen Merge-Commit handelt.
