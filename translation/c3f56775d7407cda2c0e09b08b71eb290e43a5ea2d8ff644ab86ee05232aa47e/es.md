```
LibGit2.revcount(repo::GitRepo, commit1::AbstractString, commit2::AbstractString)
```

Lista el número de revisiones entre `commit1` y `commit2` (OID de commit en forma de cadena). Dado que `commit1` y `commit2` pueden estar en diferentes ramas, `revcount` realiza una lista de revisiones "izquierda-derecha" (y cuenta), devolviendo una tupla de `Int`s - el número de commits a la izquierda y a la derecha, respectivamente. Un commit a la izquierda (o a la derecha) se refiere a qué lado de una diferencia simétrica en un árbol se puede alcanzar el commit.

Equivalente a `git rev-list --left-right --count <commit1> <commit2>`.

# Ejemplos

```julia
repo = LibGit2.GitRepo(repo_path)
repo_file = open(joinpath(repo_path, test_file), "a")
println(repo_file, "hello world")
flush(repo_file)
LibGit2.add!(repo, test_file)
commit_oid1 = LibGit2.commit(repo, "commit 1")
println(repo_file, "hello world again")
flush(repo_file)
LibGit2.add!(repo, test_file)
commit_oid2 = LibGit2.commit(repo, "commit 2")
LibGit2.revcount(repo, string(commit_oid1), string(commit_oid2))
```

Esto devolverá `(-1, 0)`.
