```
LibGit2.revcount(repo::GitRepo, commit1::AbstractString, commit2::AbstractString)
```

`commit1` ve `commit2` arasındaki revizyon sayısını listeleyin (komit OID'leri string biçiminde). `commit1` ve `commit2` farklı dallarda olabileceğinden, `revcount` "sol-sağ" revizyon listesi (ve sayımı) gerçekleştirir ve bir `Int` tuple'ı döndürür - sırasıyla sol ve sağ komitlerin sayısı. Sol (veya sağ) bir komit, bir ağaçtaki simetrik farkın hangi tarafında komitin erişilebilir olduğunu ifade eder.

Eşdeğer olarak `git rev-list --left-right --count <commit1> <commit2>`.

# Örnekler

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

Bu `(-1, 0)` döndürecektir.
