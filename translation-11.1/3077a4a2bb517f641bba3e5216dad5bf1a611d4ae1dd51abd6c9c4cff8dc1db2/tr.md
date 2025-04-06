```
@githash_str -> AbstractGitHash
```

Verilen stringden bir git hash nesnesi oluşturur, eğer string 40 onaltılık basamaktan daha kısa ise bir `GitShortHash`, aksi takdirde bir `GitHash` döner.

# Örnekler

```jldoctest
julia> LibGit2.githash"d114feb74ce633"
GitShortHash("d114feb74ce633")

julia> LibGit2.githash"d114feb74ce63307afe878a5228ad014e0289a85"
GitHash("d114feb74ce63307afe878a5228ad014e0289a85")
```
