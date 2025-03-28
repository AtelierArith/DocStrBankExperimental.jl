```
lookup_branch(repo::GitRepo, branch_name::AbstractString, remote::Bool=false) -> Union{GitReference, Nothing}
```

Bestimmen Sie, ob der durch `branch_name` angegebene Branch im Repository `repo` existiert. Wenn `remote` `true` ist, wird angenommen, dass `repo` ein entferntes Git-Repository ist. Andernfalls ist es Teil des lokalen Dateisystems.

Geben Sie entweder eine `GitReference` auf den angeforderten Branch zurück, wenn er existiert, oder [`nothing`](@ref), wenn nicht.
