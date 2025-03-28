```
@githash_str -> AbstractGitHash
```

Konstruiere ein Git-Hash-Objekt aus dem gegebenen String und gebe einen `GitShortHash` zurück, wenn der String kürzer als 40 hexadezimale Ziffern ist, andernfalls einen `GitHash`.

# Beispiele

```jldoctest
julia> LibGit2.githash"d114feb74ce633"
GitShortHash("d114feb74ce633")

julia> LibGit2.githash"d114feb74ce63307afe878a5228ad014e0289a85"
GitHash("d114feb74ce63307afe878a5228ad014e0289a85")
```
