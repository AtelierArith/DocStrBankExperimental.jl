```
GitRevWalker(repo::GitRepo)
```

Bir `GitRevWalker`, bir git deposu `repo`nun *revizyonları* (yani, commit'leri) arasında *yürür*. Bu, depodaki commit'lerin bir koleksiyonudur ve yineleme ve [`LibGit2.map`](@ref) ve [`LibGit2.count`](@ref) çağrılarını destekler (örneğin, `LibGit2.count`, bir depodaki commit'lerin ne kadarının belirli bir yazar tarafından yapıldığını belirlemek için kullanılabilir).

```julia
cnt = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.count((oid,repo)->(oid == commit_oid1), walker, oid=commit_oid1, by=LibGit2.Consts.SORT_TIME)
end
```

Burada, `LibGit2.count`, belirli bir `GitHash` ile yürüyüş boyunca commit'lerin sayısını bulur. `GitHash` bir commit'e özgü olduğundan, `cnt` `1` olacaktır.
