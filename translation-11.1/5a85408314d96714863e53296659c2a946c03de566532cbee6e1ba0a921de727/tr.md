```
lookup_branch(repo::GitRepo, branch_name::AbstractString, remote::Bool=false) -> Union{GitReference, Nothing}
```

`branch_name` ile belirtilen dalın `repo` deposunda mevcut olup olmadığını belirleyin. Eğer `remote` `true` ise, `repo` bir uzak git deposu olarak varsayılır. Aksi takdirde, yerel dosya sisteminin bir parçasıdır.

Mevcutsa istenen dala bir `GitReference` döndürün, aksi takdirde [`nothing`](@ref) döndürün.
